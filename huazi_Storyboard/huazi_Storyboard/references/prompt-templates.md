# 可复用提示词模板库

> 使用规则：模板中【方括号】为必须填写的变量，生成成品时必须全部填好；
> 填不确定时显式保留「【在此填写……】」并提示用户确认。成品中禁止残留"请自行替换"类说明。

---

## 一、资产卡版面规格模板库（资产出图·直接投喂画图模型）

> **资产卡五件套（强制）**：每个资产（人物/场景/道具）的出图提示词必须同时包含五件——
> ① 中文对照提示词（核对用） ② 英文投喂提示词（直接投喂） ③ 主形象/主视角纯图提示词（无版面简版，备用） ④ 版面排版提示词（区块比例与文字标注说明，已内嵌于①②） ⑤ 反向提示词。
> 场景资产如有变体（光照/时段/天气/状态差异），**每个变体各写一条完整独立提示词**，禁止写"其余变体同理"。
>
> **版面标注铁律**：所有资产卡为单张版面图（asset sheet），各区块比例必须显式写入提示词，全部区块带文字标注，**最左上角为资产名称或代号**。豆包 Seedream 可靠渲染短文字，标注直出；若文字崩坏，改用③纯图简版重出，版面对应关系靠人工比对。
>
> **资产命名规范（强制，三处对应缺一即返工）**：
> - 人物：`CH01-角色名`；场景：`S01-场景名-视图代码`（MV主视角 / TP三视图 / FP俯视图 / RV反打 / TD俯拍，变体为 `-V1、-V2…`）；道具：`P01-道具名`
> - 出图文件名 = 资产代号；**00 文件必须包含「资产命名与挂载对应表」**，把每个代号对应到 03 分镜提示词的 `@图片N` 和 05 视频提示词的 `@ref_image_N` / 上传顺序
> - 03 分镜写「@图片1 是 CH01-山羊头的全身形象参考图」；05 视频写「@ref_image_0｜CH01-山羊头」——**00 ↔ 03 ↔ 05 三处名称完全一致**

### 1.1 人物资产卡版面图（每角色一张）

**版面排版规格（④核对用）**
```text
16:9 横版单张画布，细线分区块，全部区块带中文小字标注：
- 最左上角：资产名称/代号文字标注（如「CH01-山羊头」）
- 左侧约 43% 宽、通高：人物全身主肖像（正面全身大图）
- 中部约 35% 宽：三视图区（正面全身 / 侧面全身 / 背面全身）
- 三视图下方：人物特点特写行（疤痕 / 胎记 / 纹身 / 标志道具等）+ 服装特写（上衣 / 裤装 / 鞋履 / 配件）
- 右侧约 22% 宽、通高：五官特写纵列四格（眉眼 / 口鼻 / 耳朵 / 发型）
- 所有区块必须是同一人物的同一张脸、同一套服装
- **背景统一浅色：纯白或浅灰最佳，禁用深色背景（深色背景会污染发丝边缘与服装色准）**
```

**中文对照提示词（①版面版·核对用）**
```text
生成一张16:9横版人物资产设定卡，画布最左上角用文字标注资产代号【CH01-角色名】。
左侧43%区域为该人物正面全身主肖像；中部35%区域为同一人物的三视图（正面全身、侧面全身、背面全身）；
三视图下方为人物特点特写（【疤痕/胎记/纹身/标志道具】）与服装特写（【上衣/裤装/鞋履/配件】）；
右侧22%区域纵排四格五官特写：眉眼特写、口鼻特写、耳朵特写、发型特写。
人物设定：【性别年龄体格】【发型发色】【五官特征】【标志特点】【服装全描述含颜色】【气质】。
所有区块必须是同一张脸、同一套服装、同一人物，区块间以细线分隔并附中文小字标注，
浅色背景（纯白或浅灰最佳），除资产代号与区块名外无其他文字，无水印。
```

**英文投喂提示词（②版面版·直接投喂）**
```text
Character asset sheet on ONE 16:9 landscape canvas, panels separated by thin hairline rules, every panel labeled with small Chinese text. TOP-LEFT CORNER: the asset code printed as a text label: "【CH01-角色名拼音】". LEFT ZONE, about 43% of the canvas width, full height: large front full-body hero portrait of the SAME character. CENTER ZONE, about 35% width: three views of the SAME character (front full-body, side full-body, back full-body); BENEATH the three views, a horizontal strip of close-up detail studies: 【特点1英文，如：a pale scar detail】 and costume close-ups (【服装件1英文】 / 【服装件2英文】 / 【配件英文】). RIGHT ZONE, about 22% width, full height, four stacked face-part close-up panels: eyebrows-and-eyes, nose-and-mouth, ear, hairstyle. Character design: 【性别年龄体格英文】; 【发型发色英文】; 【五官特征英文】; 【标志特点英文，如：a pale scar across the left eyebrow】; 【服装全描述英文】; 【气质英文】. Every panel must show the identical face, identical outfit and identical props on the SAME character. Plain light background (pure white or light grey preferred), character reference sheet, no text other than the asset code and panel labels, no watermark
```

**主形象纯图提示词（③无版面简版·备用）**
```text
Character reference sheet on ONE 16:9 landscape canvas, four views of the SAME character side by side: front full-body view, side full-body view, back full-body view, and a face close-up portrait. Character design: 【性别年龄体格英文】; 【发型英文】; 【服装英文】; 【标志道具英文】; 【气质英文】. All four views must show the identical face, identical outfit and identical props. Plain light background (pure white or light grey preferred), character sheet, no text, no watermark
```

**反向提示词（⑤人物通用，直接投喂）**
```text
different faces between views, inconsistent outfit, extra characters, crowd, text, watermark, signature, blurry face, deformed hands
```

**版面版成品示例（可对照格式检查自己的产出）**
```text
Character asset sheet on ONE 16:9 landscape canvas, panels separated by thin hairline rules, every panel labeled with small Chinese text. TOP-LEFT CORNER: the asset code printed as a text label: "CH01-shanyangtou". LEFT ZONE, about 43% of the canvas width, full height: large front full-body hero portrait of the SAME character. CENTER ZONE, about 35% width: three views of the SAME character (front full-body, side full-body, back full-body); BENEATH the three views, a horizontal strip of close-up detail studies: the goat-head mask knot texture detail and costume close-ups (black formal suit jacket / black trousers / black leather shoes). RIGHT ZONE, about 22% width, full height, four stacked face-part close-up panels: the mask eye sockets with sharp sly eyes, the mask muzzle and mouth, the mask horn and ear shape, the matted wool hair texture. Character design: a tall thin man in a formal black western suit; his head is a real goat-head mask with yellowed and blackened knotted matted wool, two hollow eye sockets revealing sharp sly eyes; a faint aura of decay. Every panel must show the identical face, identical outfit and identical props on the SAME character. Plain light grey background, character reference sheet, no text other than the asset code and panel labels, no watermark
```

### 1.2 场景资产卡版面图（每场景一张，主视角+锚点特写）

**版面排版规格（④核对用）**
```text
16:9 横版单张画布，细线分区块，全部区块带中文小字标注：
- 最左上角：资产名称/代号文字标注（如「S01-空屋-主视角MV」）
- 左侧约 72% 宽、约 70% 高：场景主视角大图（构图与成片机位一致）
- 右侧通高纵列 + 主图下方横排：场景锚点特写（每个锚点一格，特写内容必须是主图中真实存在的物件）
- 画面中没有任何人物
```

**中文对照提示词（①版面版·核对用）**
```text
生成一张16:9横版场景资产设定卡，画布最左上角用文字标注资产代号【S01-场景名-MV】。
左侧72%区域为场景主视角大图：从【观察位置】看向【核心视觉物】，画面包含【锚点1】【锚点2】【锚点3】【锚点4】【锚点5】，光照【光照方案】。
右侧与下方为场景锚点特写格：【锚点特写1】【锚点特写2】【锚点特写3】，每个特写必须是主图中真实存在的物件，
同一空间、同一材质、同一光照，不新增主图中没有的内容。
画面中没有任何人物。除资产代号与区块名外无其他文字，无水印。
```

**英文投喂提示词（②版面版·直接投喂）**
```text
Environment asset sheet on ONE 16:9 landscape canvas, panels separated by thin hairline rules, every panel labeled with small Chinese text. TOP-LEFT CORNER: the asset code printed as a text label: "【S01-scene-MV】". MAIN ZONE, left about 72% of the canvas width and 70% of its height: the master establishing view: 【场景英文总述】, 【核心视觉物英文】, 【锚点1英文】, 【锚点2英文】, 【锚点3英文】, 【锚点4英文】, 【锚点5英文】, 【光照英文】. RIGHT COLUMN, full height along the right edge, stacked close-up anchor panels: 【锚点特写1英文】, 【锚点特写2英文】. BOTTOM ROW, spanning beneath the main zone: 【锚点特写3英文】. Every anchor panel is a close-up crop of the SAME space shown in the master view — same geometry, same materials, same wear marks; nothing invented that is not present in the master view. Absolutely no people anywhere on the sheet. No text other than the asset code and panel labels, no watermark, 16:9
```

**主视角纯图提示词（③无版面简版·备用）**
```text
【场景英文总述】, 【核心视觉物英文】, 【锚点1-5英文】, absolutely no people, empty scene, 【光照英文】, cinematic composition, 16:9
```

**反向提示词（⑤场景通用，直接投喂）**
```text
people, human figures, characters, crowds, silhouettes of people, oversaturated colours, sterile showroom cleanliness, warped perspective, melted geometry, floating objects, text, watermark, signature
```

### 1.3 场景变体提示词（有变体必写，一个变体一条完整提示词）

> 变体命名：`S01-场景名-MV-V1`、`S01-MV-V2`…；V1 为主变体（默认状态）。
> 变体之间**只允许声明的差异维度发生变化**（光照/时段/天气/物件状态），其余一切（布局、材质、锚点物件）锁定与 V1 完全一致。
> 每个变体按 1.2 的完整结构（中文对照+英文+反向）各写一条；变体版面卡的左上角代号也带变体号。

**变体中文对照提示词（模板）**
```text
基于资产代号【S01-场景名-MV-V1】的主视角设定图，生成同场景的变体版设定卡，左上角标注代号【S01-场景名-MV-V2】。
唯一变化：【差异维度，如：钨丝灯骤暗，全场陷入深灰蓝暗光，仅座钟轮廓隐约可见】。
其余一切锁定不变：房间布局、四面墙与天花板地板、【锚点1】【锚点2】【锚点3】的材质与位置完全一致，画面中没有任何人物。
```

**变体英文投喂提示词（模板）**
```text
Variant asset sheet of the SAME room shown in the reference image 【S01-scene-MV-V1】, asset code label printed at the top-left corner: "【S01-scene-MV-V2】". ONLY CHANGE: 【差异维度英文，如：the tungsten bulb is at its darkest flicker moment, the whole room falls into deep grey-blue darkness with only the silhouette of the table clock barely visible】. Everything else locked identical to the reference image: room layout, four walls, ceiling and floor, same materials and positions of 【锚点1英文】【锚点2英文】【锚点3英文】, absolutely no people. No text other than the asset code, no watermark, 16:9
```

**反向提示词（场景通用）**：与 1.2 相同，直接复用。

### 1.4 场景俯视图（座位锚定的唯一事实来源，每场景必做）

**中文对照提示词（①核对用）**
```text
基于资产代号【S01-场景名-MV】的主视角设定图，生成俯视视角平面图，左上角标注代号【S01-场景名-FP】，
类似装修设计的平面图，完整呈现【关键布局物件1】、【关键布局物件2】、【关键布局物件3】的位置与相对关系。
```

**英文投喂提示词（②直接投喂）**
```text
Top-down architectural floor plan of the SAME room shown in the reference image, asset code label "【S01-scene-FP】" printed at the top-left corner, like an interior design layout plan viewed from directly above: 【物件1位置英文】, 【物件2英文】, 【物件3英文】. Accurate spatial proportions, 【N】 square meters, same materials and color palette as the reference image. No people, no text labels other than the asset code, no watermark, 16:9
```

**反向提示词（⑤直接投喂）**
```text
people, human figures, three-quarter perspective, side view, tilted perspective, warped proportions, text, watermark, signature
```

### 1.5 室内三视图（差异化构件场景必做；旋转对称场景可省略）

**中文对照提示词（①核对用）**
```text
基于资产代号【S01-场景名-MV】的场景图，生成室内三视图版面卡，左上角标注代号【S01-场景名-TP】，
分区块呈现：正面视图、背面视图、四墙全景图。画面必须包含【必须画出的物件1】【必须画出的物件2】；
不展示【排除区域】。这个【场所类型】并不大，大概只有【N】多平方。
所有视图与主视角图完全同一空间、同一材质，区块带中文小字标注，无人物，无水印。
```

**英文投喂提示词（②直接投喂）**
```text
Interior three-view asset sheet of the SAME room shown in the reference image, asset code label "【S01-scene-TP】" printed at the top-left corner, ONE 16:9 canvas divided into labeled panels: front elevation view, rear elevation view, and a full panoramic view covering all four walls. The room includes 【必须画出的物件1英文】 and 【必须画出的物件2英文】; do NOT show 【排除区域英文】. The space is small, only about 【N】 square meters, 【空间尺度特征英文】. Same geometry, same materials, same color palette as the reference image across all panels. No people, no text labels other than the asset code, no watermark, 16:9
```

### 1.6 道具资产卡版面图（贯穿道具/关键道具）

**版面排版规格（④核对用）**
```text
16:9 横版单张画布，细线分区块，全部区块带中文小字标注：
- 最左上角：道具资产代号文字标注（如「P01-座钟」）
- 左侧约 55% 宽、通高：道具主图（成片中的真实比例与质感）
- 右侧纵列 + 下方横排：锚点特写（正面 / 侧面 / 背面 / 顶部 / 材质纹理 / 与人物互动时的比例参照）
- 背景统一浅色（纯白或浅灰最佳）
```

**中文对照提示词（①版面版·核对用）**
```text
生成一张16:9横版道具资产设定卡，画布最左上角用文字标注资产代号【P01-道具名】。
左侧55%区域为道具主图：【道具全描述含材质颜色磨损】；右侧与下方为锚点特写格：
正面特写、侧面特写、材质纹理特写、与人手互动的比例参照特写。
所有特写必须是同一件道具，区块间细线分隔并附中文小字标注，浅色背景（纯白或浅灰最佳），无人物，除代号与区块名外无其他文字，无水印。
```

**英文投喂提示词（②版面版·直接投喂）**
```text
Prop asset sheet on ONE 16:9 landscape canvas, panels separated by thin hairline rules, every panel labeled with small Chinese text. TOP-LEFT CORNER: the asset code printed as a text label: "【P01-prop】". LEFT ZONE, about 55% of the canvas width, full height: the hero shot of the prop: 【道具全描述英文】. RIGHT COLUMN and BOTTOM ROW: close-up anchor panels: front detail, side detail, material texture detail, and a scale-reference panel showing the prop held by a hand. All panels show the SAME prop with identical materials and wear. Plain light background (pure white or light grey preferred), no people other than the hand in the scale panel, no text other than the asset code and panel labels, no watermark
```

**反向提示词（⑤道具通用，直接投喂）**
```text
different prop between panels, duplicated props, people, faces, text, watermark, signature, deformed proportions, floating objects
```

---

## 二、分镜图提示词模板（SOP 第 4 步核心）

### 通用骨架

```text
帮我生成4张10秒左右的真人电影级别分镜图。
1️⃣ @图片1 是【角色A】的全身形象参考图；
2️⃣ @图片2 是【角色B】的全身形象参考图；
3️⃣ @图片3 是【角色C】的全身形象参考图；（无此角色时删除本行并顺延编号）
👉 @图片4 内【场景名】空间场景逻辑参考图；

其中物理规则：
【本段人物站位与姿态，如：角色A和角色B进来之后，2人坐在靠窗边的桌子上】
【其他人物状态，如：角色C没精打采地趴在柜台的位置，避免三人同框】
【互动触发顺序，如：角色C发现两人的问话之后才开始接下来的剧情互动】
【人数上限，如：场内除了这3人以外没有任何人】
【空间大小，如：整个场景并不大，只有24个平方】
【本段特化规则：动线/朝向/不换位/贯穿道具等】

以下是故事剧情内容：
梗概：【本段剧情一句话】。
场景：【场景全名】
shot1：时长：N秒；景别：X；运镜：Y；情节描述：【画面内容】。情绪/备注：【情绪】。
shot2：……
shot3：……
shot4：……
生成结果不要有任何的字幕、备注和标识，以纯画面的形式给我即可。
```

### 段型变体（替换"其中物理规则"块的写法）

**开场段（单人/悬念）**
```text
本场画面中只有【角色A】一个清晰人物，场内不得出现任何其他清晰人物；
【角色A】【站位与动作，如：独自站在墙下仰头看牌，全程站立不动】；
【文字密集物规避，如：除"零号牌"外，其余所有号码牌一律虚化为蓝色色块纹理，不出现任何清晰数字】；
【空间要素锁定：光照、布局】。
```

**对话段（正反打·双人）**
```text
本场画面中只有【角色A】和【角色B】两个清晰人物，其余人物一律虚化、不得清晰露脸；
两人【位置关系，如：并肩站在X前方，角色B站在角色A的右侧，两人间距约半米】；
两人全程站立/落座不移动、不换位置、不换朝向；
【视线锚点，如：视线始终指向右上方墙上】；
【环境锁定】。
```

**新角色入场段（动线）**
```text
【角色C】从【入口位置】入场，沿【动线，如：中央过道】直线走到【停驻点，如：前方讲台位】，站位全程固定在【停驻点】；
【原有人物状态变化，如：入场时两人仍站在X前，随后随众人一起落座】；
【新角色与既有人物的框位约束，如：与角色A不同框近景】；
其余人物一律虚化、不得清晰露脸。
```

**收尾钩子段（动作链）**
```text
最后一张分镜为钩子帧：【具体动作链，如：一名穿X制服的工作人员（不露清晰正脸）把Y从Z处取下放进容器，再把容器放在角色A的桌上】；
【钩子帧中不得出现任何文字，字幕卡由后期制作添加】；
【其余人物与空间锁定】。
```

---

## 三、空间物理规则句式库（SOP 第 2 步用）

直接套用的标准句式：

| 目的 | 句式 |
|---|---|
| 锁人数 | "场内除了这N人以外没有任何人/没有任何其他客人或侍从" |
| 锁面积 | "整个【场所】并不大，只有N个平方" |
| 锁位置 | "【角色】坐在【方位+家具】上"／"【角色】全程固定在【位置】" |
| 锁间距 | "两人间距约半米"／"紧邻其右侧，同排相邻" |
| 锁顺序 | "【角色B】发现【事件】之后才开始接下来的剧情互动" |
| 锁框位 | "避免三人同框"／"【角色A】与【角色B】不同框近景" |
| 锁贯穿道具 | "【角色】左腕戴【道具】，全程可见，外观不变" |
| 防乱跑 | "【角色】全程坐姿/站姿不移动、不换位置、不换朝向" |
| 文字规避 | "除【X】外，其余【文字载体】一律虚化为色块纹理，不呈现清晰数字" |
| 负面总闸 | "生成结果不要有任何的字幕、备注和标识，以纯画面的形式给我即可" |

---

## 四、视频提示词五锁结构模板（SOP 第 6 步用）

```text
[项目规格]
项目：【N】秒，画幅：16:9，帧基准：24fps，真人电影级写实【题材】剧情片。
场景：【场景全名】。【N】个连续分镜，严格次序表现。
叙事链：【一句话动作链，用→连接】。
物理规则为最高优先级：【关键空间约束一句话摘要】。

[STYLE LOCK]
【风格总述，如：近未来中国纪实综艺质感／华语古装写实电影质感】：【环境材质】。
【光照：方向、时段、质感】。【色调锁定：环境色／角色A服装色／角色B服装色】，
【对比饱和胶片等画质要求】，真皮肤质感。
气氛【氛围词】。不使用【负面风格清单】。

[REFERENCE LOCK]
@ref_image_0｜【角色A】唯一人物身份参考：四视图拼版作为整体且只有一个编号，
锁定【外貌+服装全描述】。全片保持同一张脸、体型、发型与服装，不得衍生新角色、
新发型或新色卡。
@ref_image_1｜【角色B】唯一人物身份参考：（同上格式）
@ref_image_2｜【角色C】唯一人物身份参考：（同上格式）
@ref_image_N｜【场景】空间与构图逻辑参考：单文件多视图拼版（正视图、侧视图、
俯视图、平面布局、空间说明），作为整体内景唯一的制图与连贯性锚定参考；
【关键布局】是全片事实来源：空间【尺度特征】，构图不得改动或重建场景。

[PHYSICAL / CONTINUITY LOCK]
一、空间尺度：【面积、纵深、过道】；镜头不得拍成【夸大形态】。
二、人物数量：场内自始至终只有【N人】；【门外/场外排除项】。
三、贯穿锚点：【道具/服装/光照连续性要求】。
四、文字规避：【文字载体虚化规则】。

HARD CUT
[SHOT 01 | 00:00.000—00:02.500]
【景别】、【运镜】：【情节描述】。【台词镜注明：口型与中文台词严格同步："……"】。
【焦段/景深】。24fps实时，承担【情绪】。结束画面定格于【定格描述】。
（逐镜重复，总时长与项目规格一致）

[AUDIO LOCK]
含中文同期对白，无旁白、无歌声、无背景音乐。
00:00—00:05：【环境音层】。
00:05—00:10：【音效/对白时间点】。
（分时段写满全片时长）
```

**参考图上传顺序表**（随每条视频提示词附在 code block 外的说明行）：
`图1=角色A资产 → 图2=角色B资产 → 图3=角色C资产 → 图4=九宫格分镜图 → 图5=场景俯视图（锚定）`

---

## 五、豆包/大模型整理指令模板（中间环节用）

当视频平台模型需要由大模型先整理提示词时：

```text
调用插件"电影级 AI 视频提示词 V2.0"。帮我生成4张【N】秒左右的真人电影级别分镜稿。
图一是【角色A】的全身形象参考图；
图二是【角色B】的全身形象参考图；
图三是【角色C】的全身形象参考图；
图四【场景】空间场景逻辑参考图；

其中物理规则：
（粘贴对应段物理规则块）

以下是故事剧情内容：（粘贴对应段 shot 表）
```

---

## 六、风格提示词词库（第 0 步风格确认后，全项目统一使用）

> **使用规则**：第 0 步确认风格后，把所选风格的【风格标注】与【英文投喂词】追加到本项目**每一条**资产卡/分镜图/视频提示词中（资产卡加在提示词末尾，分镜任务指令替换"真人电影级别"字样，五锁 [STYLE LOCK] 首行即风格总述）；【反向提示词】追加到各资产反向提示词末尾。全项目只用一种风格，不得混用。

| 风格 | 风格标注（中文） | 英文投喂词（追加用） | 配套反向提示词（追加用） |
|---|---|---|---|
| 电影写实风（默认） | 真人电影级写实 | photorealistic live-action cinematic film still, real skin texture, filmic color grading, shot on cinema camera | anime, cartoon, 3D render, CGI look, illustration, painting, video game character |
| 3D动漫风 | 3D动漫风格电影级 | 3D stylized anime movie style, cel-shaded 3D render, anime proportions in 3D, high quality toon-shaded CGI, cinematic lighting | photorealistic, live-action photo, real skin pores, hyperrealism |
| 3D真人风（写实CG） | 3D写实CG电影级 | hyperrealistic 3D character render, Unreal Engine 5 cinematic realism, realistic CGI human, subsurface skin shading, cinematic lighting | anime, cartoon, toon shading, illustration, painting |
| 2D动漫风 | 2D动漫风格电影级 | 2D Japanese anime key visual style, anime film illustration, clean lineart, cinematic anime lighting | photorealistic, live-action, 3D render, western cartoon |
| 国漫风 | 国漫风格电影级 | Chinese donghua animation movie style, xianxia/modern donghua character design, cinematic donghua lighting | photorealistic, live-action photo, american cartoon style |

**各环节插入位置**：
- 资产卡（人物/场景/道具）：英文投喂提示词末尾追加 `【英文投喂词】`；中文对照末尾写明【风格标注】
- 分镜图：任务指令首句替换为"帮我生成4张10秒左右的【风格标注】分镜图"
- 视频五锁：`[STYLE LOCK]` 首行写"【风格标注】质感：…"
- 00 文件头部必须有一行"本资产风格声明：【风格标注】"，全文件提示词均已按该风格编写
