# Site Lookup

此算子为特定领域专用算子，不建议使用；
具体功能如下:
- 根据用户配置的资产树查询售电的场站属性信息，目前只用于售电场景;
- 查询场站属性中area、etype、 vlevel和date，其中date为数据record中的时间(/time)字段数据,组合后数据格式为:
    - {"area":2900,"date":"2019-07-23","etype":"eType1|eType2|eType3|eType4","vlevel":2};
    - 查询场站属性中etype组成为eType1、eType2、eType3和eType4
    - 如果查询到的eType为空(0)，则不会被放进etype中
- 查询实例所处的场站信息:
    - 如果查询的场站信息位于资产树中实例往上的第一层，则能查询到场站信息;
    - 如果查询的场站信息位不于资产树中实例往上的第一层，则查询到场站信息为空;
    - 如果查询的实例不在资产树上，则查询到场站信息为空;
- 不支持血缘


## Configuration

该算子的配置包括General、SiteLookup的详细信息，各字段的配置如下：

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


### SiteLookup

.. list-table::

   * - 名称
     - 是否必须
     - 描述
   * - treeTag
     - Yes
     - 查找规则，由于上一条更新数据信息是打在每一条record上的，所以每一条规则需设置要附加上一条更新数据属性信息的测点，最终结果需要用输出点进行承载，输入输出点必须模型一致；可增、删、改规则
   * - QualityControl Level
     - No
     - 根据数据质量过滤处理数据，只有符合质量条件的record才会进行此次处理


## Output Results

运行的结果将包装到/attr/siteLookup字段中,如果/attr/siteLookup为空Map，则未查询到数据;各字段的描述如下：

.. list-table::

   * - 名称
     - 是否必须
     - 描述
   * - /attr/siteLookup
     - Map
     - 测点属性信息对象
   * - site
     - String
     - 查询场站属性中area、etype、 vlevel和date，其中date为数据record中的时间(/time)字段数据,组合后数据格式为:{"area":2900,"date":"2019-07-23","etype":"eType1","vlevel":2};


### Output Example

**配置示例**

.. image:: media/site_lookup_config.jpg

**输出示例**

.. image:: media/site_lookup_result.jpg

<!--end-->
