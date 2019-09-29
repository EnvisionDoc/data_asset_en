# Data Quality Overview
Data has become a new type of important asset that Internet enterprises rely on. Data quality is directly related to the accuracy of information and also the survival and competitiveness of an enterprise.

Data quality management refers to a set of processing guidelines for measuring, improving, and verifying data quality as well as integrating organizational data. The IoT data is featured by large volume, high speed, and diversity so that the data processing required to ensure the quality of IoT big data is different from the quality management ways as stated in the traditional data management plans.

## Data Quality Assessment Dimensions
Currently, EnOS supports the following data quality assessment dimensions:
- Completeness

  Data is complete and dose not miss any information. For example, the personnel information data should completely cover gender, age, and the measuring point data of the day should be fully uploaded.

- Accuracy

  Data is accurate and reasonable. For example, the personnel age information should be within a reasonable range.

- Timeliness

  Data is uploaded to the cloud in time with no latency.

For a detailed description of the data quality dimensions and a review of the data quality report, see [Managing Data Quality](../howto/quality/managing_data_quality).

## Product Advantages

- Multi-dimensional data quality assessment
- Visualized data quality report query

## Usage Limit
- Data quality rules are set by configuring relevant stages in stream data processing jobs.