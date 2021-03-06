# Point Partitioner

 不建议使用，因为此算子功能已被算子Partitioner包含；
具体功能如下:
- 按点(/pointId)字段进行分区;属于同一设备、同一测点的record会被分到同一个分区内
- 不支持血缘

## Configuration

该算子的配置包括General、Partitioner的详细信息，各字段的配置如下：

### General

.. list-table::

   * - 名称
     - 是否必须
     - 描述
   * - Name
     - Yes
     - 算子名称
   * - Description
     - No
     - 算子描述
   * - Stage Library
     - Yes
     - 算子所属的库
   * - Required Fields
     - No
     - 数据必须包含的字段，如果未包含指定字段，则record将被过滤掉
   * - Preconditions
     - No
     - 数据必须满足的前提条件，如果不满足指定条件，则record将被过滤掉
   * - On Record Error
     - Yes
     - 对错误数据的处理方式  Discard:直接丢弃；Send to Error：发送至错误中心；Stop Pipeline：停止流任务运行


### Partitioner

.. list-table::

   * - 名称
     - 是否必须
     - 描述
   * - Parallelism (Standalone Mode Only)
     - Yes
     - standalone模式下本stage需要worker数量
   * - Application Name (Standalone Mode Only)
     - Yes
     - standalone模式下本stage的运行Application name，默认值为：SDC Spark App
   * - Init Method Arguments
     - Yes
     - 无效配置项


## Output Results

该算子的输出结果为进行分区后的records


### Output Example
.. image:: media/point_partitioner_result.jpg

<!--end-->
