---

1. 所有命令文件需要放在 `ff_resource\com.freejoy.ff\quick_cmd\`
2. 文件名需要为 `*.cmds` 才会出现在控制台里
3. 文件名里不能有空格
4. 命令是大小写无关的
5. 参数中有等号的表示可选参数，不填时使用等号后的默认值。例如可以只写 
`AddHero 35 2`，效果与 `AddHero 35 2 1` 一样。

---

```
RunFile {filename}, {start_line = 0}, {delay_time = 0}
Delay {time(ms)}
WaitCallback {type} // dungeon:0, 

// Hero Command
AddHero {id}, {grade = 0}, {count = 1} 
AddHeroRange {from}, {to}, {grade = 0}, {count = 1}
AddEidolon {id}, {count = 1}
AddEidolonRange {from}, {to}, {count = 1}
AddHeroExp {index[1~5]}, {value}
SetHeroLevel {index[1~5]}, {value}
SetAllHeroLevel {value}
SetCurrentHeroLevel {value} // 仅在英雄信息界面有效
SetHeroGrade {index[1~5]}, {value}
SetCurrentHeroGrade {value} // 仅在英雄信息界面有效
SetHeroSkillLevel {index[1~5]}, {skillpos[1~4]}, {level}
SetCurrentSkillLevel {skillpos[1~4]}, {level} // 仅在英雄信息界面有效
SetAllHeroesSkillLevel {skillpos[1~4]}, {level}
SetBattleHero {index[1~5]}, {id} // id = -1 表示主英雄，0 表示下阵（未来可能会失效）。该功能将指定 id 的最强英雄放到相应的槽位（首先背包得有这个英雄）
SetBattleHeroes {id1}, {id2}, {id3}, {id4}, {id5}
SetBattleEidolon {id}
SetBattleHeroIndices {pos1}, {pos2}, {pos3}, {pos4}, {pos5}, {type = 0} // type 的枚举值详见 BattlePositionType
RemoveHeroes {quality} // 删除品质小于等于 quality 的所有英雄

// Item Command
AddItem {id}, {count = 1}
AddItemRange {from}, {to}, {count = 1}
RemoveAllItems
AddEquipment {id}, {strengthen = 0}, {refine = 0}, {count = 1} 
AddEquipmentRange {from}, {to}, {strengthen = 0}, {refine = 0}, {count = 1}

// Role Command
AddExp {value}
AddCash {value}
AddMoney {value}
AddVipExp {value}
AddPrestige {value}
AddTowerPoint {value}
AddFactionMoney {value}
AddMilitaryMoney {value}
AddActivityPoint {value}
AddAchievementPoint {value}
SetVipLevel {value}
SetMilitaryRank {value}

// Dungeon Command
FinishDungeon {id}, {star = 3} // star 是通关星星数，star = 0 表示未通关，下同
FinishDungeonTo {id}, {star = 3}
FinishChapters {difficulty[normal:0, hard:1]}, {star = 3}
FinishAllChapters {star = 3}
ResetDailyPlayTimes {id} // 重置副本次数

// Battle Command
EnterBattle {id} // 进入副本
FinishBattle {time(ms) = 0} // 达到指定时间后结束战斗
HidePartners {toggle[off:0, on:1]}
SetButcherMode {toggle[off:0, on:1]}
SetPlayerAttackable {toggle[off:0, on:1]}
Suicide // 自杀
FullRage // 怒气值全满
ResetEidolon
CastSkill {id}, {level = 1} // 主动技
AddPassiveSkill {id} // 被动技
RemovePassiveSkill {id}
SetDestinyPassiveSkill {toggle[off:0, on:1]}
AddBuff {id}
RemoveBuff {id}
SetMonsterHp {percent[1~100] = 100}
SpawnMonster {id}, {count = 1}, {distance = 3000}, {radius = 0} // distance, radius 是以 1000 为一个单位，即 100 表示 0.1 个单位
StartStats // 开始战斗统计
SaveStatsToFile // 保存战斗统计
SetFightStatus {mode[Manual:0, AutoAttack:1, AutoSkill:2]}
SetAutoCastUltiSkill {toggle[off:0, on:1]}
SetAutoCastEidolon {toggle[off:0, on:1]}

// Task Command
ShowTask
ClearAllTasks
ClearFinishedTasks
AddTask {id}
RemoveTask {id}
FinishTask {id}
ForbidNoviceTutorials
ForbidBattleTutorials

// Audio Command
PlayAudio {name}

// FFTest Command
CallHero {id}
CallPlayer {count}
SetHeroToRobot {level}
SetMoveRadius {radius} // 以 1000 为一个单位，即 100 表示 0.1 个单位
SetInvalidRadius {radius} // 以 1000 为一个单位，即 100 表示 0.1 个单位
SetArenaAttackerData {id1, ..., id5, lv1, ..., lv5, grade, skill_level}
SetArenaDefenderData {id1, ..., id5, lv1, ..., lv5, grade, skill_level}
DebugChat {channel}, {message} // World:1, Guild:3, Team:4, Current:5

// Time Command
SetSpeed {value = 100}
SetFps {value = 30}

// Equipment Command
PutOn {id}, {heropos[1~5]}
Strengthen {heropos[1~5]}, {slotpos[1~6]}, {level} // level 仅供参考，一般会超过
Refine {heropos[1~5]}, {slotpos[1~6]}, {times}
```