# Forgont 

## Wikipedia extraction with LLMs
- `wikipedia` folder contains all the files of the experiment. 
- `wikipedia/corpus` folder contains the input dataset storing 64 description of forgeries from Wikipedia
- `wikipedia/forgont_extraction_pipeline.ipynb` is a notebook containing the code of the pipeline
- `wikipedia/from_json_to_graph_converter.ipynb` is a notebook containing the code to conver JSON files into RDF
- `wikipedia/outputs/` folder contains all intermediate JSON files and the RDF produced by the pipeline

## Austrian catalogue extraction
- `catalogue` folder contains all the files to convert Haider catalogue from .docx to RDF
- `catalogue_converter.ipynb` is a notebook containing all scripts to convert the data
- `forgont-kb.trig` contains the RDF produced by the data conversion

## Ontology

### Document Types
1. *Charter*
2. *Letter*
3. *Map*
4. *Manuscript*
5. *Printed Book*
6. *Codex*
7. *Certificate*

### Juridical Categorisation of Document Types

![Hierarchy of Documents](grafoo/document_definition.svg)

1. **Document**: A document is a recorded or written representation of information, often in written or digital form.

2. **Original**: An original refers to the initial or primary version of a document, created directly by the author or source which is also deemed to be authentic.

3. **Alleged Original**: An alleged original is a document that is claimed to be the original but may be subject to dispute or doubt.

5. **Copy**: A copy is a reproduction or duplicate of an original document, often made to distribute or preserve information.

6. **Authentic Copy**: An authentic copy is a duplicate of an original document that is verified to be genuine and accurate.

7. **Insert**: An insert is additional content or material added into an existing document.

8. **Imitative Copy**: An imitative copy is a reproduction of an original document created with the intent to closely mimic the original.

9. **Simple Copy**: A simple copy is a straightforward duplication of an existing document without any attempt to alter or mimic the original.

10. **Forgery**: Forgery refers to the act of creating or altering a document, signature, or object with the intent to deceive or defraud by passing it off as genuine.

11. **Suspected Forgery**: A suspected forgery is a document or item that is believed to be a result of forgery, but its authenticity has not been confirmed.

12. **Integrally Forged Document**: An integrally forged document is one that has been entirely fabricated or altered, often to deceive others.

13. **Partially Forged Document**: A partially forged document is one in which only a portion of the content has been fabricated or altered, while other parts remain genuine.

### Authenticity assessments 

- **Authenticity Assessment claim** This contains the conclusions of the scholarly analysis
  - Location of creation assignment
  - Time of creation assignment
  - Author assignment
  - Physical document type assignement

  - **Fuzziness handling**:
    - Fuzzy dates are recorded as timespans
    - Qualifiers are added to each triple of the claim GRAPH

- **Critical discourse representation** This contains the analysis performed by the scholar to reach a certain conclusion and some contextual information
  - Author of the claim
  - Documentary features on which the scholarly analysis is based on
  - Criteria adopted by the scholar to perform the analysis (e.g. Radio-carbon testing)
  - Approach adopted by the scholar to perform the analysis (e.g. Scientific analysis)
  - Evidence detected by the scholar to support that the document is a forgery (e.g. Presence of subsequent interpolations)
  - Source of the claim 
  - Other claims or Editions considered as being the background of the claim

![Authenticity assessment claim representation](grafoo/forgont-model.svg)

### Object Properties
#### Claim object properties
- **forgont:has_author**: The author of the claim
- **forgont:has_background**: The scholarly background of the scholar
- **forgont:analysed_feature**: The document features analysed by the scholar
- **forgont:based_on_evidence**: Describes the evidences collected to support the claim conclusion 
- **forgont:criteria**: Describes the criteria (or analysis) used to reach the conclusion declared by the claim
- **forgont:consider_compared_document**: Describe the set of documents which has been compared to the one under analysis described by the claim
- **provo:has_source**: Describe the set of sources on which the claim has been based on
- **forgont:based_on**: Describe the source on which the claim has been published
- **provo:approach**: The approach adopted by the scholar to claim such conclusion

### Features
#### Estrinsic features - Medium:
- ink   
- support 
- sigillum (or seal)
- document authentication marks
- handwriting

#### Intrinsic features - Contents and Structure
- metre and style 
- orthography 
- inter-punctuation 
- indentation 
- legal formulas 
- terminology 
- document structure
- format - spacing 
- format - signs 
- format - interpolations
- chronology and dating 
- document content
- illustration

#### Context
- historical context
- list of witnesses
- document provenance

### Evidence
  - **Anachronistic extrinsic features**: Presence of anachronistic materials or inconsistencies in material properties within the purported time
  - **Inconsistent usage of extrinsic features**: Verification of the consistency of use of materials within the surveyed document
  - **Absence of expected extrinsic features**: Verification of extrinsic characteristics, attributes, or elements are not present as typically observed.
  - **Anachronistic usage of intrinsic features**: Incorrect or inappropriate use of language, terms, or elements within the document.
  - **Inconsistent usage of intrinsic features**: Check for consistency within the document regarding dates, events, and details. Internal contradictions may raise questions about authenticity
  - **Content lack of credibility**:  The reliability and trustworthiness of the information presented in the document.
  - **Anachronistic contents**: The contents described in the document seem to be referenced or inspired by later documents.
  - **Unverified historical contents**: Information within the document that has not been adequately confirmed or supported by reliable historical sources.
  - **Inconsistent contents within the document**: Check for consistency within the document regarding dates, events, and details described in the document. Internal contradictions may raise questions about authenticity
  - **Inconsistent contents with other documents**: Lack of coherence or agreement in content when compared to information presented in other historical documents.
  - **Presence of subsequent interpolations**: Inclusion of additional elements or modifications within a given context. It refers to the introduction of supplementary information following an initial statement or passage.
  - **Incomplete Provenance**: If there are gaps or missing links in the origin or chain of custody, the provenance is considered incomplete. This may raise questions about the document's authenticity and reliability.
  - **Disputed Provenance**: If there are conflicting accounts or disputes regarding the origin or chain of custody, the provenance is considered disputed. This may require further investigation to resolve inconsistencies.
  - **Doubtful Provenance**: If there are reasonable doubts about the authenticity of the provenance, it is categorized as doubtful. This could be due to inconsistencies, lack of supporting evidence, or questionable sources.
  - **Document Loss**: If the historical document is confirmed to be lost or missing, it affects the provenance. In such cases, efforts to recover or reconstruct the provenance become crucial.
  - **Inconsistency in Testimonies**: Look for consistency in the testimonies of multiple witnesses. Consistent accounts strengthen the reliability of the provenance, while conflicting or inconsistent statements may raise doubts.
  - **Lack of genuine witnesses**: Assess the credibility of the witnesses. Consider factors such as their expertise, reliability, and potential biases. Reliable witnesses with firsthand knowledge or expertise in relevant fields enhance the credibility of the document's provenance.

### Criteria [to do]
#### Qualitative document analysis
- **Witness Testimony Criteria**
- **Other criteria**
  - **Documentary Evidence Criteria**
  - **Holistic Assessment**: Scholars emphasize a holistic approach, considering the collective weight of evidence. While individual criteria contribute to the assessment, scholars recognize the need to balance positive indicators with potential red flags.
  - **Expert Involvement**: Depending on the complexity of the document, scholars may involve experts in relevant fields (historians, archivists, forensic experts) to provide specialized insights and analysis.

#### Scholarly Approach
- Scientific analysis
- Historical analysis
- Philologic analysis
- Diplomatic analysis
- Literary analysis








