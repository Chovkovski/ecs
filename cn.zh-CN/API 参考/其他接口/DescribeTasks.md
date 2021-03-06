# DescribeTasks {#DescribeTasks .reference}

查询指定的异步请求的进度。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeResourcesModification|
|RegionId|String|是|地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|TaskAction|String|是|任务操作的接口名称。取值范围：-   ImportImage：导入镜像（[ImportImage](intl.zh-CN/API参考/镜像/ImportImage.md#)）
-   ExportImage：导出镜像（[ExportImage](intl.zh-CN/API参考/镜像/ExportImage.md#)）

|
|TaskIds|String|否|任务 ID，单次最多支持指定 100 个，ID 之间使用半角逗号（`,`）分隔。|
|TaskStatusrf|String|否|任务状态。取值范围：-   Finished：已完成
-   Processing：运行中
-   Pending：等待执行
-   Deleted：已取消
-   Paused：暂停

默认值：无目前，只支持状态为 `Finished` 和 `Processing` 的任务进展，填入其他取值将不会生效。

|
|StartTime|String|否|按创建时间查询，创建时间区间的起始点。时间类型按照 [ISO8601](intl.zh-CN/API参考/附录/时间格式.md#) 标准表示，并需要使用UTC 时间。格式为：YYYY-MM-DDThh:mmZ。|
|EndTime|String|否|按创建时间查询，创建时间区间的终止点。时间类型按照 ISO8601 标准表示，并需要使用 UTC 时间。格式为：YYYY-MM-DDThh:mmZ。|
|PageNumber|Integer|否|查询结果的页码，起始值为 1，默认值为 1。|
|PageSize|Integer|否|分页查询时设置的每页记录数，最大值 100 行，默认值为 10。|

## 返回参数 {#section_ay2_4yg_ydb .section}

|名称|类型|描述|
|:-|:-|:-|
|TaskSet|[TaskType](intl.zh-CN/API参考/数据类型/TaskType.md#)|任务集合|
|RegionId|String|地域 ID。|
|TotalCount|Integer|列表条条目数|
|PageNumber|Integer|当前页码|
|PageSize|Integer|当前分页包含多少条目|

## 示例 {#section_mv1_byg_ydb .section}

**请求示例**

```

https://ecs.aliyuncs.com/?Action=DescribeTasks
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例**

**XML 格式**

```

<DescribeTasksResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>2</TotalCount>
  <PageSize>2</PageSize>
  <RegionId>cn-hangzhou</RegionId>
  <RequestId>E5C82807-5588-4661-9A96-350B206A7623</RequestId>
  <TaskSet>
    <Task>
      <CreationTime>2015-11-24T12:50Z</CreationTime>
      <FinishedTime>2015-11-24T12:50Z</FinishedTime>
      <SupportCancel>true</SupportCancel>
      <TaskAction>IMPORT_IMAGE</TaskAction>
      <TaskStatus>Finished</TaskStatus>
      <TaskId>t-23mo8zf9w</TaskId>
    </Task>
    <Task>
      <CreationTime>2015-11-23T15:10Z</CreationTime>
      <FinishedTime>2015-11-23T15:16Z</FinishedTime>
      <SupportCancel>true</SupportCancel>
      <TaskAction>IMPORT_IMAGE</TaskAction>
      <TaskStatus>Finished</TaskStatus>
      <TaskId>t-23sgu0dyj</TaskId>
    </Task>
  </TaskSet>
</DescribeTasksResponse>

```

**JSON 格式**

```
{
    "PageNumber": 1,
    "TotalCount": 2,
    "PageSize": 2,
    "RegionId": "cn-hangzhou",
    "RequestId": "F746C690-D9EA-4F87-AF31-8E1910FAB541"，
    "TaskSet": {
        "Task": [
            {
                "CreationTime": "2015-11-24T12:50Z",
                "FinishedTime": "2015-11-24T12:50Z",
                "SupportCancel": true,
                "TaskAction": "ImportImage",
                "TaskStatus": "Finished",
                "TaskId": "t-23mo8zf9w"
            },
            {
                "CreationTime": "2015-11-23T15:10Z",
                "FinishedTime": "2015-11-23T15:16Z",
                "SupportCancel": true,
                "TaskAction": "ImportImage",
                "TaskStatus": "Finished",
                "TaskId": "t-23sgu0dyj"
            }
        ]
    }
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|MissingParameter|An input parameter “RegionId” that is mandatory for processing the request is not supplied.|400|缺少必填参数 `RegionId`。|
|InvalidRegionId.NotFound|The specified region not found.|400|指定的 `RegionId` 不存在。|

