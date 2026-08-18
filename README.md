# Milk Run WebGIS Demo

一个面向汽车零部件入厂循环取货的前端演示应用。所有计算在浏览器本地完成，不需要后端服务。

## 功能

- 地图选点：设置工厂、添加供应商并编辑需求与时间窗。
- CSV 导入：批量导入供应商经纬度、重量、体积、时间窗和服务时间。
- 模拟求解：基于重量/体积容量约束和最近邻规则生成多条循环取货线路。
- 输出：路线、车辆、访问顺序、到达/离开时刻、里程、工时、成本和装载率。
- 评估：KPI 对比、综合评分、时间窗/容量/工时异常定位。

## 本地运行

```powershell
npm install
npm run dev
```

浏览器访问 Vite 输出的本地地址（通常为 `http://localhost:5173`）。

## CSV 字段

```text
id,name,lat,lng,demandKg,demandM3,windowStart,windowEnd,serviceMin
```

- `lat`、`lng`：WGS84 经纬度。
- `demandKg`：需求重量（kg）。
- `demandM3`：需求体积（m³）。
- `windowStart`、`windowEnd`：`HH:mm`。
- `serviceMin`：现场服务时间（分钟）。

示例文件见 `sample-suppliers.csv`。

## 说明

当前求解器是用于讲标演示的前端启发式版本。正式项目可将“运行优化”替换为异步后端 API，并接入 GA、ALNS、NSGA-II、滚动优化和企业道路矩阵。
