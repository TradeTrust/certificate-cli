# Document CLI tool

## Setup

```bash
npm install -g @govtechsg/tradetrust-cli
```

The above command will install the tradetrust CLI to your machine. You will need to have node.js installed to be able to run the command. 

## Batching Documents

This command process all documents in the input directory and issue all of them in a single
batch. It will then add the signature to the individual documents.

```bash
tradetrust batch <PathToUnsignedDocuments> <PathToSignedDocuments>
```

Example:

```bash
tradetrust batch ./documents/raw-documents/ ./documents/processed-documents/

2019-02-11T08:37:44.848Z info: Batch Document Root: 0xf51030c5751a646284c898cff0f9d833c64a50d6f307b61f2c96c3c838b13bfc
```

## Batching PDFs

This command process all PDFs in the input directory and convert all of them into the base64 string. It will then appned this base64 string as an attachment to the given document.

```bash
tradetrust batch-pdf <PathToRawPDFsDir> <PathToRawDocumentFile>
```

Example:

```bash
tradetrust batch-pdf ./documents/raw-pds/ ./documents/sample.json
```

## Verifying All Signed Document in a Directory

This command verifies that the document (and all it's evidence) is valid and is part of the document batch. However, it does not verify that the batch's merkle root is stored on the blockchain. User will need to verify that the document has indeed been issued by checking with the issuer's smart contract.

```bash
tradetrust verify-all <PathToDocument>
```

Example:

```bash
tradetrust verify-all ./documents/processed-documents

2019-02-11T08:38:36.767Z info: All documents in ./documents/processed-documents is verified
```

## Verifying Single Signed Document
sign
This command verifies that the document (and all it's evidence) is valid and is part of the document batch. However, it does not verify that the batch's merkle root is stored on the blockchain. User will need to verify that the document has indeed been issued by checking with the issuer's smart contract.

```bash
tradetrust verify <PathToDocument>
```

Example:

```bash
tradetrust verify ./documents/processed-documents/urn:uuid:08b1f10a-6bf0-46c8-bbfd-64750b0d73ef.json

2019-02-11T08:41:17.301Z info: Document's signature is valid!
2019-02-11T08:41:17.302Z warn: Warning: Please verify this document on the blockchain with the issuer's document store.
```

## Document privacy filter

This allows document holders to generate valid documents which hides certain evidences. Useful for hiding grades lol.

```bash
tradetrust filter <inputDocumentPath> <outputDocumentPath> [filters...]
```

Example:

```bash
tradetrust filter signed/example1.json signed/example1.out.json transcript.0.grade transcript.1.grade

2019-02-11T08:43:50.643Z info: Obfuscated document saved to: signed/example1.out.json
```

## Version

```
tradetrust --version
```

## Test

```
npm run test
```
