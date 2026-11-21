# 原始资料约定

captures.parquet 的 device/boot/sequence 唯一表示采样事件，asset_hash只表示文件内容。bursts.csv 给协议内同一设备连续间隔阈值秒数。clock.csv 的 offset_seconds 加到设备时间，适用device/boot/sequence闭区间。
deployments.csv 有site/region/round及UTC左闭右开有效期；uptime.csv 只证明所列连续运行区间。transects.csv 的km和hours是人工努力量，绝不等同camera_hours。
identifications.jsonl 带opinion、capture_key、taxon、confidence、status及supersedes；taxonomy.jsonl 的rename可全映射，split必须由evidence_mapping逐记录确认。protocols.json定义最低confidence、是否接受上级类群和努力单位。public_grid.csv 是站点公开区域映射，不改变内部region。
clock revision较大替代同device/boot/序列范围；部署和uptime已经是UTC，不再二次校正。连拍在同部署与协议下按修正后相邻事件间隔判断，不跨部署边界合并。

所有名称与数值均为本地合成数据，不代表真实企业、监管结论或生态调查。data/catalog.json 保存文件哈希、原始行数与列；data/updates/ 为后到修订资料，可独立接收。JSON null 表示尚无该值，不与数值零等同；CSV保留原字符串，金额和数量应按十进制解释。来源身份相同且内容相同的重送不产生新业务事实，同身份版本不同内容需保留争议，除明确替代关系外不按到达顺序判定权威。

privacy.json列出需位置粗化的类群；公开查询对这些类群使用public_grid映射，其他类群沿用原站点显示。此映射不影响内部轮次及努力量计算。
