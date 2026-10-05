# Procedural Correspondence Archive

## Purpose

This directory preserves the procedural correspondence generated during the
doctoral examination of the candidate's portfolio. It provides an auditable
record of communications among the candidate, the Doctoral Examiners, the
academic administration, and the Board of Academic Directors.

The correspondence archive documents the sequence through which technical
observations were communicated, responses and revised manuscripts were
received, and examination issues were resolved or carried forward.

## Directory structure

```text
09_procedural_correspondence/
├── README.md
├── general/
├── P01/
│   ├── round-01/
│   ├── round-02/
│   ├── round-03/
│   └── final/
├── P02/
│   ├── round-01/
│   ├── round-02/
│   └── final/
├── P03/
├── P04/
├── P05/
└── P06/
```

Additional rounds may be created whenever required by the examination record.
The `general/` directory is reserved for correspondence concerning the
portfolio as a whole, procedural arrangements, or matters that cannot be
assigned to one submitted work.

## Participant codes

| Code | Participant |
|---|---|
| `CAN` | Candidate |
| `EX01` | Ezequiel, Doctoral Examiner |
| `EX02` | Sara, Doctoral Examiner |
| `EXAMINERS` | Ezequiel and Sara acting jointly |
| `ADM` | Academic administration |
| `BOARD` | Board of Academic Directors |

## Correspondence identifiers

Every communication must receive a stable identifier in chronological order
within the relevant submitted work:

```text
COR-P01-001
COR-P01-002
COR-P02-001
```

Communications concerning the portfolio as a whole use:

```text
COR-GEN-001
```

Identifiers must not be reused, even if a file is later withdrawn, superseded,
or determined to have been registered incorrectly.

## Filename convention

Use the following pattern:

```text
COR-[WORK]-[SEQUENCE]_[YYYY-MM-DD]_[SENDER]-to-[RECIPIENT]_[TYPE].[ext]
```

Examples:

```text
COR-P01-001_2026-09-21_EX02-to-CAN_EMAIL.eml
COR-P01-001_2026-09-21_EX02-to-CAN_EMAIL.pdf
COR-P01-002_2026-09-23_CAN-to-EXAMINERS_EMAIL.pdf
COR-P01-003_2026-09-27_EX01-to-CAN_LETTER.pdf
COR-P01-004_2026-09-30_CAN-to-EXAMINERS_NOTICE.pdf
```

Permitted type codes include:

- `EMAIL`: individual email message;
- `LETTER`: formal letter;
- `MEMO`: memorandum;
- `NOTICE`: notice of submission, revision, or deposit;
- `ACK`: acknowledgement of receipt;
- `THREAD`: complete email chain;
- `TRANSCRIPT`: transcription of another communication medium.

For an exported email thread, use:

```text
COR-P01-THREAD-001_2026-09-21_to_2026-09-30.pdf
```

Whenever possible, preserve the individual messages in addition to the
consolidated thread.

## Archival formats

For material email correspondence, retain:

1. the original `.eml` file, including headers and metadata;
2. a PDF rendering for convenient consultation and citation; and
3. every material attachment as a separately registered file.

Both the `.eml` and PDF rendering may share the same correspondence identifier
because they are different archival representations of the same communication.
Screenshots should be used only when the original message cannot be exported.

## Treatment of attachments

Correspondence folders record the transmission of an attachment but are not
the primary location of substantive examination documents.

- Submitted and revised manuscripts belong in
  `01_candidate_submission/papers/`.
- Technical reports belong in
  `02_technical_evaluations/paper_level/`.
- Formal examiner questions belong in `03_examiner_questions/`.
- Candidate responses belong in `04_candidate_responses/`.
- Post-response assessments belong in `05_post_response_assessment/`.

The correspondence register must identify every transmitted attachment and
its authoritative repository location. Files should not be duplicated merely
to reproduce the contents of an email attachment.

## Examination rounds

Rounds describe procedural stages rather than manuscript version numbers:

- `round-01`: initial reports or questions and the candidate's first response;
- `round-02`: evaluation of the first response or revision and any subsequent
  communication;
- `round-03` and later: additional exchanges where required;
- `final`: the final deposited version, closure communication, or final
  procedural acknowledgement.

A single round may refer to more than one manuscript version. Conversely, a
new manuscript version does not automatically create a new correspondence
round.

## Correspondence register

Every archived communication must be entered in:

```text
08_registers/correspondence-register.csv
```

The register should contain at least:

```csv
correspondence_id,work_id,date,time_zone,sender,recipients,communication_type,subject,round,related_report_ids,related_finding_ids,related_question_ids,related_document_ids,attachments,archival_filename,status,sha256
```

Dates and times should preserve the metadata of the original communication.
The relevant time zone must be recorded whenever a precise transmission time
is material.

## Relationship to examination records

Correspondence is procedural evidence and does not replace the substantive
documents to which it refers. Each record should link, where applicable, to:

- the technical report that originated the observation;
- the relevant finding or findings;
- the formal question communicated to the candidate;
- the candidate's response;
- the revised manuscript;
- the post-response assessment; and
- the final resolution record.

The intended chain of traceability is:

```text
Technical report
    -> Finding
    -> Formal question
    -> Correspondence
    -> Candidate response or revised manuscript
    -> Post-response assessment
    -> Resolution
```

## Integrity and version-control rules

1. Received and sent correspondence is immutable and must never be overwritten.
2. Original files must be preserved even when a PDF rendering or transcription
   is produced.
3. A corrected transcription must receive its own version identifier, for
   example `COR-P01-001_TRANSCRIPT-v2.pdf`.
4. The original communication remains authoritative over any transcription.
5. Every file must be committed with a descriptive message and registered with
   a SHA-256 checksum.
6. Sensitive credentials, personal identification documents, or unrelated
   personal information must not be committed to the repository.
7. Redacted copies must be clearly marked as redacted and must not overwrite
   the restricted original.

## Suggested commit messages

```text
Create procedural correspondence archive
Archive P01 correspondence round 01
Register P02 candidate response correspondence
Archive final P06 correspondence
```

## Access and publication rule

The internal repository is the authoritative archive. If a communication is
copied to the candidate-exchange repository, it must retain the same
correspondence identifier. The correspondence register should indicate that a
shared copy exists. Publication, external disclosure, or inclusion in the
Board package requires an explicit procedural decision and must not occur
automatically merely because the document is stored in this directory.
