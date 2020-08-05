# EDH Kafka Consumer

从Kafka队列中消费数据，作为pipeline处理数据的来源。该算子属于EDH Streaming Common Library。


## Configuration

该算子的配置包括 **General**，**Kafka**，**Data Format** 的详细信息，各字段的配置如下：

### General

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - 名称
     - 是否必须
     - 描述
   * - Name
     - Yes
     - 算子名称
   * - Description
     - No
     - 算子描述
   * - On Record Error
     - Yes
     - 对错误数据的处理方式，可选：

       + Discard：直接丢弃
       + Send to Error：发送至错误中心
       + Stop Pipeline：停止流任务运行

### Basic

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - 名称
     - 是否必须
     - 描述
   * - Quality Filter
     - No
     - 根据数据质量过滤处理数据，只有符合质量条件的record才会进行此次处理

### Input/Output

.. list-table::
   :widths: 30 20 50
   :header-rows: 1

   * - 名称
     - 是否必须
     - 描述
   * - Input Point
     - Yes
     - 设置待处理的模型和测点列表，格式为：{模型标识}::{测点标识}


## Output Results

经过该算子的所有Record都会被存入Redis。

### Output Example

.. image:: media/record_capturer_result.png

<!--end-->
