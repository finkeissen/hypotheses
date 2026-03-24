Envelope Schema: Hypotheses → Matrix (SELF-CONTAINED)
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "hypotheses-matrix-output.schema.json",
  "title": "Hypotheses → Matrix Output Envelope (self-contained)",
  "type": "object",
  "additionalProperties": false,
  "required": ["interface", "hypotheses_context", "binding", "runs", "artifacts"],
  "properties": {
    "interface": {
      "type": "object",
      "additionalProperties": false,
      "required": ["name", "version", "produced_at"],
      "properties": {
        "name": { "const": "hypotheses-matrix-output" },
        "version": { "type": "string", "description": "SemVer. Breaking changes bump MAJOR." },
        "produced_at": { "type": "string", "format": "date-time" },
        "generator": { "type": "string" },
        "notes": { "type": "string" }
      }
    },

    "hypotheses_context": {
      "type": "object",
      "additionalProperties": false,
      "required": ["hypotheses_commit"],
      "properties": {
        "hypotheses_commit": { "type": "string" },
        "contract": {
          "type": "object",
          "additionalProperties": false,
          "required": ["id", "version"],
          "properties": {
            "id": { "type": "string" },
            "version": { "type": "string" }
          }
        }
      }
    },

    "binding": {
      "type": "object",
      "additionalProperties": false,
      "required": ["input_snapshot_id"],
      "properties": {
        "input_snapshot_id": { "type": "string", "minLength": 1 },
        "input_snapshot_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" }
      }
    },

    "runs": {
      "type": "array",
      "items": { "$ref": "#/$defs/hyp_run_manifest_v1" },
      "minItems": 1
    },

    "artifacts": {
      "type": "object",
      "additionalProperties": false,
      "required": ["hypotheses", "tests", "conflicts", "logs"],
      "properties": {
        "hypotheses": { "$ref": "#/$defs/artifact_collection" },
        "tests":      { "$ref": "#/$defs/artifact_collection" },
        "conflicts":  { "$ref": "#/$defs/artifact_collection" },
        "logs":       { "$ref": "#/$defs/artifact_collection" }
      }
    },

    "integrity": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "bundle_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" },
        "counts": { "type": "object", "additionalProperties": { "type": "integer", "minimum": 0 } }
      }
    }
  },

  "$defs": {
    "artifact_collection": {
      "type": "object",
      "additionalProperties": false,
      "required": ["format", "items"],
      "properties": {
        "format": { "type": "string", "enum": ["INLINE_JSON_ARRAY", "JSONL_URI", "OTHER"] },
        "items": {
          "type": "array",
          "items": { "$ref": "#/$defs/hyp_artifact_v1" },
          "default": []
        },
        "uri": { "type": "string" },
        "content_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" }
      },
      "allOf": [
        {
          "if": { "properties": { "format": { "const": "JSONL_URI" } }, "required": ["format"] },
          "then": { "required": ["uri"] }
        }
      ]
    },

    "hyp_run_manifest_v1": {
      "type": "object",
      "additionalProperties": false,
      "required": ["run_id", "created_at", "outcome", "binding"],
      "properties": {
        "run_id": { "type": "string", "minLength": 1 },
        "created_at": { "type": "string", "format": "date-time" },
        "outcome": { "type": "string", "enum": ["SUCCESS", "NOCLAIM", "UNKNOWN", "CONFLICT", "STOP"] },

        "binding": {
          "type": "object",
          "additionalProperties": false,
          "required": ["input_snapshot_id"],
          "properties": {
            "input_snapshot_id": { "type": "string", "minLength": 1 }
          }
        },

        "failure": {
          "type": "object",
          "additionalProperties": false,
          "required": ["code", "message", "blame"],
          "properties": {
            "code": {
              "type": "string",
              "enum": [
                "SNAPSHOT_INVALID",
                "ADMISSIBILITY_MISSING",
                "SCHEMA_INVALID",
                "POLICY_BLOCKED",
                "INTERNAL_ERROR",
                "UNKNOWN"
              ]
            },
            "message": { "type": "string" },
            "blame": { "type": "string", "enum": ["INPUT", "SCHEMA", "GENERATOR", "POLICY", "UNKNOWN"] },
            "evidence_refs": { "type": "array", "items": { "type": "string" } }
          }
        }
      },

      "allOf": [
        {
          "if": { "properties": { "outcome": { "enum": ["STOP", "UNKNOWN"] } }, "required": ["outcome"] },
          "then": { "required": ["failure"] }
        }
      ]
    },

    "hyp_artifact_v1": {
      "type": "object",
      "additionalProperties": true,
      "required": ["run_id", "artifact_id"],
      "properties": {
        "run_id": { "type": "string", "minLength": 1 },
        "artifact_id": { "type": "string", "minLength": 1 },
        "content_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" },

        "artifact_type": {
          "type": "string",
          "enum": ["HYPOTHESIS", "TEST", "CONFLICT", "LOG", "OTHER"]
        },

        "depends_on": {
          "type": "array",
          "items": { "$ref": "#/$defs/matrix_ref_v1" }
        }
      }
    },

    "matrix_ref_v1": {
      "type": "object",
      "additionalProperties": false,
      "required": ["snapshot_id", "run_id", "artifact_id"],
      "properties": {
        "snapshot_id": { "type": "string", "minLength": 1 },
        "run_id": { "type": "string", "minLength": 1 },
        "artifact_id": { "type": "string", "minLength": 1 },
        "content_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" }
      }
    }
  }
}


## 6) Envelope Schema: Predictions → Hypotheses (SELF-CONTAINED)

{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "predictions-hypotheses-output.schema.json",
  "title": "Predictions → Hypotheses Output Envelope (self-contained)",
  "type": "object",
  "additionalProperties": false,
  "required": ["interface", "predictions_context", "binding", "runs", "artifacts"],
  "properties": {
    "interface": {
      "type": "object",
      "additionalProperties": false,
      "required": ["name", "version", "produced_at"],
      "properties": {
        "name": { "const": "predictions-hypotheses-output" },
        "version": { "type": "string", "description": "SemVer. Breaking changes bump MAJOR." },
        "produced_at": { "type": "string", "format": "date-time" },
        "generator": { "type": "string" },
        "notes": { "type": "string" }
      }
    },

    "predictions_context": {
      "type": "object",
      "additionalProperties": false,
      "required": ["predictions_commit"],
      "properties": {
        "predictions_commit": { "type": "string" },
        "contract": {
          "type": "object",
          "additionalProperties": false,
          "required": ["id", "version"],
          "properties": {
            "id": { "type": "string" },
            "version": { "type": "string" }
          }
        }
      }
    },

    "binding": {
      "type": "object",
      "additionalProperties": false,
      "required": ["input_set_id"],
      "properties": {
        "input_set_id": { "type": "string", "minLength": 1 },
        "input_set_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" }
      }
    },

    "runs": {
      "type": "array",
      "items": { "$ref": "#/$defs/pred_run_manifest_v1" },
      "minItems": 1
    },

    "artifacts": {
      "type": "object",
      "additionalProperties": false,
      "required": ["predictions", "verifications", "conflicts", "logs"],
      "properties": {
        "predictions":   { "$ref": "#/$defs/artifact_collection" },
        "verifications": { "$ref": "#/$defs/artifact_collection" },
        "conflicts":     { "$ref": "#/$defs/artifact_collection" },
        "logs":          { "$ref": "#/$defs/artifact_collection" }
      }
    },

    "integrity": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "bundle_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" },
        "counts": { "type": "object", "additionalProperties": { "type": "integer", "minimum": 0 } }
      }
    }
  },

  "$defs": {
    "artifact_collection": {
      "type": "object",
      "additionalProperties": false,
      "required": ["format", "items"],
      "properties": {
        "format": { "type": "string", "enum": ["INLINE_JSON_ARRAY", "JSONL_URI", "OTHER"] },
        "items": {
          "type": "array",
          "items": { "$ref": "#/$defs/pred_artifact_v1" },
          "default": []
        },
        "uri": { "type": "string" },
        "content_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" }
      },
      "allOf": [
        {
          "if": { "properties": { "format": { "const": "JSONL_URI" } }, "required": ["format"] },
          "then": { "required": ["uri"] }
        }
      ]
    },

    "pred_run_manifest_v1": {
      "type": "object",
      "additionalProperties": false,
      "required": ["run_id", "created_at", "outcome", "binding"],
      "properties": {
        "run_id": { "type": "string", "minLength": 1 },
        "created_at": { "type": "string", "format": "date-time" },
        "outcome": { "type": "string", "enum": ["SUCCESS", "NOCLAIM", "UNKNOWN", "CONFLICT", "STOP"] },

        "binding": {
          "type": "object",
          "additionalProperties": false,
          "required": ["input_set_id"],
          "properties": {
            "input_set_id": { "type": "string", "minLength": 1 }
          }
        },

        "failure": {
          "type": "object",
          "additionalProperties": false,
          "required": ["code", "message", "blame"],
          "properties": {
            "code": {
              "type": "string",
              "enum": [
                "HYPOTHESIS_SET_INVALID",
                "SCHEMA_INVALID",
                "POLICY_BLOCKED",
                "INTERNAL_ERROR",
                "UNKNOWN"
              ]
            },
            "message": { "type": "string" },
            "blame": { "type": "string", "enum": ["INPUT", "SCHEMA", "GENERATOR", "POLICY", "UNKNOWN"] },
            "evidence_refs": { "type": "array", "items": { "type": "string" } }
          }
        }
      },

      "allOf": [
        {
          "if": { "properties": { "outcome": { "enum": ["STOP", "UNKNOWN"] } }, "required": ["outcome"] },
          "then": { "required": ["failure"] }
        }
      ]
    },

    "pred_artifact_v1": {
      "type": "object",
      "additionalProperties": true,
      "required": ["run_id", "artifact_id"],
      "properties": {
        "run_id": { "type": "string", "minLength": 1 },
        "artifact_id": { "type": "string", "minLength": 1 },
        "content_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" },

        "artifact_type": {
          "type": "string",
          "enum": ["PREDICTION", "VERIFICATION", "CONFLICT", "LOG", "OTHER"]
        },

        "depends_on": {
          "type": "array",
          "items": { "$ref": "#/$defs/hyp_ref_v1" }
        },

        "verification_conditions": {
          "type": "object",
          "additionalProperties": true,
          "description": "Opaque structural declaration of how/when this prediction can be verified."
        }
      }
    },

    "hyp_ref_v1": {
      "type": "object",
      "additionalProperties": false,
      "required": ["set_id", "run_id", "artifact_id"],
      "properties": {
        "set_id": { "type": "string", "minLength": 1 },
        "run_id": { "type": "string", "minLength": 1 },
        "artifact_id": { "type": "string", "minLength": 1 },
        "content_hash": { "type": "string", "pattern": "^[a-f0-9]{64}$" }
      }
    }
  }
}


## 7) Minimal Fixtures (recommended)

**Input fixtures (Hypotheses → Predictions)**
hyp_set.minimal.json (1 set, 1 hypothesis)
hyp_set.conflict.minimal.json (set includes conflict ref)
hyp_set.tests.minimal.json (set includes tests)

**Output fixtures (Predictions → Hypotheses)**
pred_run.success.minimal.json (1 run, 1 prediction, verification_conditions present)
pred_run.stop.minimal.json (STOP with failure localization, logs present, no predictions)
pred_run.verification.minimal.json (prediction + verification artifact emitted)
These fixtures serve as contract-tests for both repos.

Quelle: :contentReference[oaicite:0]{index=0}

