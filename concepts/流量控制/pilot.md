#### Pilot

Pilot负责管理Istio服务网格中部署的Envoy实例的生命周期。

![](file:///Users/dengqiaoling/Accumulation/lstio/PilotAdapters.svg?lastModify=1503113281) .                                        ![](/assets/PilotAdapters.png)

如上图所示，Pilot维护了独立于底层平台的网格中的服务的规范表示。Pilot中的平台特定适配器负责适当填充此规范模型。例如，Pilot中的Kubernetes适配器实现必要的控制器来watch Kubernetes的api-server，以更改pod注册信息，入口资源以及存储流量管理规则的第三方资源。该数据被翻译成规范表示。基于规范表示生成envoy的配置。

Pilot公开了用于服务发现，动态更新到负载平衡池和路由表的API。这些API将Envoy从平台特有的细微差别中解脱出来，简化了设计并提升了跨平台的可移植性。

操作员可以通过Pilot的Rules API指定高级流量管理规则。这些规则被翻译成低级配置，并通过发现API分发到Envoy实例



  


