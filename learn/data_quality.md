# Data Quality Overview

<br />

Data has become a new type of important asset that Internet enterprises rely on and the quality of the data is directly related to the accuracy of information and also the survival and competitiveness of an enterprise.

<br />

Data quality management refers to a set of processing guidelines for measuring, improving, and verifying data quality as well as integrating organizational data. The characteristics of the large volume, fast speed, and diversity of IoT data determine the processing requirements for the quality of IoT big data, which is different from the quality management methods of traditional data management.

## Data Quality Assessment Dimensions
Currently, EnOS supports the following data quality assessment dimensions.

- Completeness

  Data is complete and no information is missed. For example, the personnel information data should completely cover gender, age, and the measurement point data of the day should be fully uploaded.

- Accuracy

  Data is accurate and acceptable. For example, the age of the personnel should be within an acceptable range.

- Timeliness

  Data is uploaded to the cloud with no latency.

<br />

For a detailed description of the data quality dimensions and review the data quality report, see [Viewing the Data Quality Report](../howto/quality/managing_data_quality).

## Product Advantages

- Multi-dimensional data quality assessment
- Visualized data quality report query

## Usage Limit
The data quality rules are set by configuring the relevant stages in the stream data processing jobs.
