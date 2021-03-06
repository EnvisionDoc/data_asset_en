# TSL Parent Asset Lookup

支持查找资产树上指定资产的父节点信息

具体功能如下：
- 支持通过资产树标签查找指定的资产树
- 支持查询输入点对应的资产的父节点信息
- 支持查询自定义节点的父节点信息
- 默认针对符合模型条件的节点，只向上查找一层父节点信息
- 详细信息封装在输入record的/attr/tslParentLookup中

## Configuration

该算子的配置包括General，Basic，Config的详细信息，各字段的配置如下：

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


### Basic

.. list-table::

   * - 名称
     - 是否必须
     - 描述
   * - Input Output
     - Yes
     - 查找规则，由于父节点信息是打在每一条record上的，所以每一条规则需设置要附加父节点信息的测点，最终结果需要用输出点进行承载，输入输出点必须一致；可增、删、改规则
   * - Input Model::Point
     - Yes
     - 单条规则的输入点，即需要附加父节点信息的测点
   * - Output Model::Point
     - Yes
     - 单条规则的输出点，即承载输出结果的测点
   * - QualityControl Level
     - No
     - 根据数据质量过滤处理数据，只有符合质量条件的record才会进行此次处理


### Config

.. list-table::

   * - 名称
     - 是否必须
     - 描述
   * - Tag::Value
     - Yes
     - 资产树标签tag id及value，用以查找资产树
   * - Enable User-Defined
     - No
     - 不建议使用此功能
   * - User-Defined Asset Id
     - No
     - 不建议使用此功能


## Output Results

该算子的输出结果包含在Attribute结构体中，各字段的描述如下：

.. list-table::

   * - 名称
     - 数据类型
     - 描述
   * - /attr/tslParentLookup
     - List<Parent>
     - 父节点信息对象
   * - List index
     - Int
     - 父节点编号
   * - parent.treeId
     - String
     - 父节点所属treeId
   * - parent.assetId
     - List<attributeId>
     - 父节点的assetId
   * - parent.attributes
     - List<tagId>
     - 父节点上绑定的属性Id 列表
   * - parent.tags
     - String
     - 父节点上绑定的标签 Id 列表
   * - parent.timezone
     - String
     - 父节点上绑定的时区



### Output Example
.. image:: media/tsl_parent_asset_lookup_result.jpg

<!--end-->
