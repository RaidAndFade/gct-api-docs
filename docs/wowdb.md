# Data Structs

It was very hard to organize this. Please forgive me for it's ugliness.

Protip : Don't bother scrolling. Just use the menu and the links.

## - Major Types
---
## -> Item 

Field | Description
--- | ---
`Integer` Id | The id of the item
`Integer` FileId | The id of the resourcefile for the icon
`String` IconFile | The relative path of the item's icon
`String` Desc | The item's description
`Integer` Quality | The item's [quality](#item-qualities)
`Array<Integer>` QualityColor | An RGB representation of the item's quality. [R,G,B]
`Integer` Bonding | The bonding style of this item (None, Pickup, Equip, Use, Quest)
[`ItemRequirements`](#item-requirements) Required | The item's requirements
`Integer` ItemLevel | The base itemlevel of this item
[`ItemType`](#item-type) ItemType | The type of this item
[`Array<SocketType>`](#socket-types) Sockets | the sockets of this item
`Object` Pricing | the price of selling/buying this item in copper (Struct : {`Buy`:`Long`,`Sell`:`Long`})
[`Array<ItemEffect>`](#item-effect) Effects | The effects of this item.

---
## -> Spell

Field | Description
--- | ---
`Integer` Id | The id of the spell
`String` Name | The name of the spell
`String` UDesc | The unclean (With variables) description of the spell
`Integer` MiscID | The ID of the spell's misc data
`Integer` DescID | The ID of the spell's extra description variable calculations
[`SpellMisc`](#spell-misc) Misc | The spell's misc data
`String` IconFile | The relative path of the spell's icon
`Array<Range>` Range | The two ranges of the spell (Each Range is [`Integer Minimum`,`Integer Maximum`] where both ints are ingame yards)
`Object` CastTime | The cast times of the spell in milliseconds (Struct : {`Base`:`Integer`,`Minimum`:`Integer`,`Per-Level`:`Integer`})
`Integer` Duration | The duration of the spell's effects in milliseconds
[`Array<SpellEffect>`](#spell-effect) Effects | The effects of this spell

---
## -> Mount

Field | Description
--- | ---
`Integer` Id | The id of the mount
`String` Name | The name of the mount
`String` Desc | The description of the mount
`String` Source | Where to get the mount from
`String` UncleanSource | Unclean source.
`Integer` Spell | The id of the spell that this mount is summoned by
`String` IconFile | The relative path of this mount's icon

---
## -> Faction

Field | Description
--- | ---
`Integer` Id | The id of this faction
`String` Name | The name of this faction
`String` Desc | The description of this faction

---
## -> Skill

Field | Description
--- | ---
`Integer` Id | The id of this skill
`String` Name | The name of this skill
`String` OriginalName | The base name of this skill
`String` Desc | The description of this skill
`String` OriginalDesc | The base description of this skill
`Integer` IconFileID | The ID of this skill's icon
`String` IconFile | The relative path to this skill's icon
`Integer` CategoryId | This id of skill's category [(List of all categories)](#skill-categories)
`String` Category | This skill's category
[`Array<SkillAbility>`](#skill-ability) Abilities | This skill's possible abilities (if this skill is a profession, these are possible recipies)

---
## -> Title

Field | Description
--- | ---
`Integer` Id | The id of this title
`Object` Name | The en_us locale'd strings for male and female
`String` Name[Male] | The male representation of this title (With %s as name placeholder)
`String` Name[Female] | The female representation of this title (With %s as name placeholder)

---
## -> Achievement

Field | Description
--- | ---
`Integer` Id | The Id of this achievement
`String` Name | The name of this achievement
`String` Desc | The description of this achievement
`String` Reward | The reward of this achievement
`Integer` Points | The points rewarded from this achievement
`String` Instance | The instance this achievement is for/from (or null)
[`Achievement`](#-achievement) Parent | This achievement's parent (or null)
[`AchievementCategory`](#achievement-category) Category | This achievement's category 
`Integer` IconFileID | The id for this achievement's icon
`String` IconFile | The relative path to this achievement's icon
[`CriteriaTree`](#criteria-tree) CriteriaTree | This achievement's criteriatree
[`Array<Criteria>`](#criteria) Criteria | This achievement's criteria

---
## -> Quest

Field | Description
--- | ---

---
### Item Type

Field | Description
--- | ---
`Integer` ClassId | The ID of the class type
`Integer` SubClassId | The ID of the subclass type
`String` Name | The type name
`String` FullName | The full type name (May be the same as name depending on class)
`String` Class | The class
`String` SubClass | The subclass

---
### Item Effect

Field | Description
--- | ---
`String` SpellID | The spell id of the effect
`Integer` Cooldown | The cooldown of the effect in milliseconds (or -1 if no cooldown)
`Integer` CategoryCooldown | The cooldown of the effect's category in milliseconds (or -1 if no cooldown)
`Integer` Charges | The number of repeats this effect can have (or -1 if unlimited)
`Integer` Category | The cateogry ID of this effect
`Integer` ChrSpecializationID | The required specialization of this effect
`Integer` OrderIndex | The order index of this effect amongst others on the same item
[`EffectTrigger`](#effect-triggers) Trigger | The trigger type of this effect

---
### Item Requirements

Field | Description
--- | ---
`Array<Integer>` Class | Class ids of classes which are allowed
`Integer` Spell | Required Spell's Id
`Integer` Level | Required Level
`Integer` Honor | Required Honor Rank
`Integer` City  | Required City Id?? (Unknown)
`Object` Skill | Required Skill & Rank (Struct : {`Id`:`Integer`,`Rank`:`Integer`})
`Object` Reputation | Required reputation & rank (Struct : {`Id`:`Integer`,`Rank`:`Integer`})

---
### Spell Misc

Field | Description
--- | ---
`Integer` m_ID | The ID of this misc data
`Long` Attributes_1 | Various flags that apply to the spell
`Long` Attributes_2 | Various flags that apply to the spell
`Long` Attributes_3 | Various flags that apply to the spell
`Long` Attributes_4 | Various flags that apply to the spell
`Long` Attributes_5 | Various flags that apply to the spell
`Long` Attributes_6 | Various flags that apply to the spell
`Long` Attributes_7 | Various flags that apply to the spell
`Integer` Speed | Unknown
`Integer` MultistrikeSpeedMod | Unknown
`Integer` CastingTimeIndex | The index of the casting time of the spell that this is misc for
`Integer` DurationIndex | The index of the duration of the spell that this is misc for
`Integer` RangeIndex | The index of the range of the spell that this is misc for
`Integer` SchoolMask | The school type of the effects of this spell
`Integer` IconFileDataID | The ID of this spell's icon
`Integer` ActiveIconFileDataID | The ID of this spell's icon when toggled on (or 0 if this spell isn't togglable)

---
### Spell Effect

Field | Description
--- | ---
`Long` maskA | Various flags that apply to this effect
`Long` maskB | Various flags that apply to this effect
`Long` maskC | Various flags that apply to this effect
`Long` maskD | Various flags that apply to this effect
`Integer` m_Id | The ID of this spell effect
`Integer` effect | The type of effect that this is [(List of all here)](#effect-types)
`Integer` auraId | The type of aura that this has [(List of all here)](#aura-types)
`Integer` basePoints | The default value of this effect (purpose based on effect type)
`Integer` effectIndex | The position of this effect amongst other effects on this spell
`Integer` miscValue_1 | The first misc value (purpose based on effect type)
`Integer` miscValue_2 | The second misc value (purpose based on effect type)
`Integer` auraName | Unknown purpose
`Integer` radiusId | The ID of this effect's radius
`Integer` target_1 | Allowed Targets (or 0 if all)
`Integer` target_2 | Allowed Targets? (or 0 if all)
`Integer` unknown_1 | Unknown (Appears in some effect types)
`Integer` unknown_2 | Unknown (Appears in some effect types)
`Integer` unknown_3 | Unknown (Appears in some effect types)
`Float` unknown_4 | Unknown (Appears in some effect types)
`Integer` effectAmplitude | The amplitude of the effect's baseValue 
`Float` unknown_5 | Unknown 
`Float` chainAmplitude | The decrease in amplitude per jump (used for spells like chain-lightning and chain-heal)
`Integer` unknown_6 | Unknown (Appears in some effect types)
`Integer` dieSides | The number of sides that the RNG of this spell has. (This + baseValue = maxValue)
`Integer` itemType | The item that this effect is associated with (purpose based on effect type)
`Integer` unknown_7 | Unknown (Appears in some effect types)
`Float` unknown_8 | Unknown
`Float` realPointsPerLevel | Unknown purpose
`Integer` triggerSpell | The spell that this effect is associated with (purpose based on effect)
`Float` unknown_9 | Unknown
`Integer` unknown_10 | Unknown
`Float` unknown_11 | Unknown
`Float` bonusMultiplier | Unknown purpose

---
### Skill Ability

Field | Description
--- | ---
`Integer` m_ID | The ID of this ability
`Integer` SpellID | The spell that is cast when this ability is used
`Integer` RaceMask | This ability's racemask
`Integer` SupercedesSpell | The spell that this requires before it can be learned
`Integer` SkillLine | The skill that this is an ability for
`Integer` MinSkillLineRank | The rank that is required in the skill before this can be learned/used
`Integer` TrivialSkillRankHigh | The rank of skill at which this rewards extra skillups
`Integer` TrivialSkillRankLow | The rank of skill at which this no longer rewards skillups
`Integer` UniqueBit | Unknown
`Integer` TradeSkillCategoryID | Unknown
`Integer` AquireMethod | Unknown
`Integer` NumSkillUps | The base number of skillups from this ability
`Integer` Unknown703 | Unknown
`Integer` ClassMask | This abiity's classmask

---
### Achievement Category

Field | Description
--- | ---
`Integer` Id | The ID of the category
`String` Name | The name of the category
[`AchievementCategory`](#achievement-category) Parent | The parent of this category (or null)

---
### Criteria Tree

Field | Description
--- | ---
`Integer` Id | The ID of this tree
`String` Description | The description of this tree
`Integer` Amount | The amount required by this tree
[`CriteriaTree`](#criteria-tree) Parent | This tree's parent

---
### Criteria

Field | Description
--- | ---
`Integer` CriteriaId | The ID of this criteria
`String` Description | The description of this criteria
`Integer` Quantity | The amount required by this criteria
`Integer` AssetId | The ID of this criteria's asset
`Integer` Type | This criteria's type [(List of known types)](#criteria-types)
`Integer` Flags | This criteria's flags
`Integer` AchievementId | This criteria's parent achievement
`Integer` CriteriaIndex | This criteria's order index

---
### Skill Categories

Id | Name
--- | ---
5| Attributes
6| Weapon Skills
7| Class Skills
8| Armor
9| Secondary Professions
10| Languages
11| Primary Professions
12| Hidden

---
### Criteria Types

Id | Name | Asset | Extra
--- | --- | --- | ---
0|Monster Kill | Creature ID |
1|Winning PvP Objective | | Holding all bases/flags
7|Weapon Skill|skill Id?|
8|Another Achievement|Achievement ID|
9|Completing Quests|Quest ID?|Global
10|Daily Quest Completion Repeatedly|Quest ID|Quantity is most likely required days.
11|Quest Completion in area|Area ID?|Quantity is required quest #
14|Completing Daily Quests||
27|Completing a Quest|Quest ID|
28|Getting spell cast on you|Spell ID|
29|Casting spell|Spell ID|Often for crafting
30|PvP Objective||flags,assaulting,defending
31|PvP Kills in BG||
32|Winning ranked arena matches in specific arena|Arena's Map ID?|
34|Owning a specific battle pet?|Spell ID|(assumed name, from The Squashling)
35|PvP kills while under influence of something||
36|Aquiring Soulbound Item|Item ID|
37|Winning Arenas||
41|Eating/Drinking specific food|Item ID|
42|Fishing things up|Item ID|
43|Exploration|Location ID
45|Purchasing 7 bank slots|
46|Exalted Reputation|Faction ID?|
47|5 Reps to exalted||
49|Equip Item of quality|Slot ID|Quality is probably in flags somewhere
52|Killing specific class||
53|Killing a specific race|Race ID?|
54|Use Emote on target|Emote ID?|
56|Being a Wrecking ball in alterac valley||
62|Getting gold from quests||
67|Looting gold|
68|Reading books|
70|Killing players||World PvP
72|Fishing things from school/wreckage||
73|Killing Mal'Ganis on Heroic||
75|Obtaining Mounts|Mount ID?|
109|Fishing in general/specific location|Location ID?|
110|Casting spells on specific targets|Spell ID|
112|Learning Cooking Recipe||
113|Honorable Kills||

---
### Effect Types

Id| Name | Has Aura? | Is Procedural? | Miscvalue Type | Extra Info
---|---|---|---|---|---
0|Unknown|0|0||
1|Instakill|0|0||
2|School Damage|0|0||
3|Serverside Script|0|0||
5|Teleport|0|0||
6|Apply Aura|1|0||
7|Environment Damage|0|0||
8|Drain Power|0|0||
9|Drain Health|0|0||
10|Heal|0|0||
11|Bind Hearth|0|0||
12|Portal|0|0||
13|Unknown|0|0||
14|Increase Max Currency|0|0|Currency|
15|Unknown|0|0||
16|Complete Quest|0|0|Quest|
17|Weapon Damage|0|0||
18|Ressurect with % Health and Mana|0|0||
19|Extra Attacks|0|0||
20|Can Dodge|0|0||
21|Can Evade|0|0||
22|Can Parry|0|0||
23|Can Block|0|0||
24|Create Item|0|0||
25|Can Use Weapon|0|0||
26|Knows Defense Skill|0|0||
27|Persistent Area Aura|1|1||Procedural?
28|Summon|0|0|Creature|
29|Blink|0|0||
30|Give Power|0|0|PowerType|
31|Weapon Damage %|0|0||
32|Trigger Missile|0|0|Missile|
33|Open Object|0|0||
34|Transform Item|0|0||
35|Apply Area Aura|1|0||
36|Learn Spell|0|0||
37|OBSOLETE|0|0||
38|Dispell|0|0|School|
39|Learn Language|0|0|Language|
40|Dual Wield|0|0||
41|Jump to Target|0|0||
42|Jump Behind Target|0|0||
43|Teleport Target to Caster|0|0||
44|Learn Skill Step|0|0|Skill|
45|Give Honor|0|0|Amount?|
46|Spawn Effect|0|0||
47|Trade Skill|0|0||
48|Base Stealth|0|0||
49|Base Detect Stealth|0|0||
50|Summon Object|0|0|GameObject|
52|Unknown|0|0||
53|Enchant Item|0|0|Enchant|
54|Enchant Item - Temporary|0|0|Enchant|
55|Tame Creature|0|0||
56|Summon Pet|0|0|Creature|
57|Learn Spell - Pet|0|0||
58|Deal Weapon Damage + Offset|0|0||
59|Open and Fast loot|0|0||
60|Proficiency|0|0||
61|Send Script Event|0|0|Script|
62|Power Burn|0|0||unknown 4 is the % burn
63|Threat|0|0||
64|Trigger Spell|0|0||
65|Apply Area Aura|1|0||
66|Create or Recharge Item|0|0||
67|Heal to Full|0|0||
68|Interrupt Target|0|0||
69|Distract|0|0||
70|Distract Move|0|0||
71|Pickpocket|0|0||
72|Far Sight|0|0||
73|Forget Talents|0|0||
74|Use Glyph|0|0||
75|Mechanical Heal|0|0||
76|Summon Object - Temporary|0|0|GameObject|
77|Script|0|0||
78|Serverside Script|0|0||
79|Abort Pending Attacks|0|0||
80|Set or Add Follower iLvl|0|0||
81|Push Spell To Bar|0|0||
82|Bind Sight|0|0||
83|Duel|0|0||
84|Unstuck|0|0||
85|Summon Target Player|0|0||
86|Activate Object|0|0||
87|Siege Damage|0|0||
88|Repair Building|0|0||
89|Siege Building Action|0|0||
90|Kill Credit|0|0|Creature|
91|Unknown|0|0||
92|Enchant Held Item|0|0|Enchant|
93|Unknown|0|0||
94|Self Ressurect With %|0|0||
95|Skin Mob|0|0||
96|Charge|0|0||
97|Summon Totems|0|0||
98|Knock Back|0|0||
99|Disenchant|0|0||
100|Intoxicate|0|0||
101|Feed Pet|0|0||
102|Dismiss Pet|0|0||
103|Increase Reputation|0|0|Reputation|
104|Drop Trap|0|0|GameObject|
105|Survey - Archeology|0|0||
106|Place Raid Marker|0|0||
107|Loot Nearby Corpse|0|0||
108|Dispell Magic|0|0|School|
109|Ressurect Pet with %|0|0||
111|Damage Durability?|0|0||
112|Unknown|0|0||
113|Unknown|0|0||
114|Taunt|0|0||
115|Durability Damage %|0|0||
116|Remove PvP Insignia|0|0||
117|AoE Ressurect with %|0|0||
118|Learn Skill|0|0|Skill|
119|Apply Aura - Pet|1|0||
121|Weapon Damage with Offset|0|0||
122|Unknown|0|0||
123|Quest Flight Path|0|0||
124|Pull|0|0||
125|Unknown|0|0||
126|Spell Steal|0|0||
127|Prospect|0|0||
128|Apply Aura <2>|1|0||
129|Apply Aura <3>|1|0||
130|Transfer Threat|0|0||
131|Play Sound|0|0|Sound|
132|Play Music|0|0|Sound|
133|Unlearn Spell|0|0||
134|Kill Credit|0|0||
135|Call Pet|0|0||
136|Heal Target for %|0|0||
137|Get % Total Power|0|0||
138|Jump|0|0||
139|Abandon Quest|0|0|Quest|
140|Cast Spell on Behalf of Target onto Self|0|0||
141|Unknown|0|0||
142|Trigger Spell with Value|0|0||
143|Apply Aura - Pet Owner|1|0||
144|Area Knockback|0|0||
145|Suspend Gravity|0|0||
146|Activate Rune|0|0||
147|Fail Quest|0|0|Quest|
148|Unknown|0|0||
149|Charge to Object|0|0||
150|Start Quest|0|0|Quest|
151|Validate Summon|0|0||
152|Summon Friend|0|0||
153|Pet??|0|0|Creature|
154|Learn Flight Path|0|0|FlightPath|
155|Titan's Grip|0|0||
156|Add Socket to Item|0|0|Enchant|
157|Create Tradeskill Item|0|0||
158|Milling|0|0||
159|Rename Pet|0|0||
160|Unknown|0|0||
161|Change Talent Spec Count|0|0||
162|Switch Spec|0|0||
163|Obliterate|0|0||
164|Cancel Area|0|0||
165|Deal % School Damage|0|0||
166|Give Currency|0|0|Currency|
167|Update Player Phase|0|0||
168|Allow Control Pet|0|0||
169|Destroy Item|0|0||
170|Update Player Auras|0|0||
171|Summon Object|0|0|GameObject|
172|Mass Ressurection|0|0||
173|Unlock Guild Bank Slot|0|0||
174|Unknown Effect With Aura|1|0||
175|Unknown|0|0||
176|Unknown|0|0||
177|Unknown|0|0||
178|Unknown|0|0||
179|Create Area Trigger|0|0||
180|Update Area Trigger|0|0||
181|Unknown|0|0||
182|Unknown|0|0||
183|Unknown|0|0||
184|Give Reputation|0|0|Reputation|
185|Unknown|0|0||
186|Unknown|0|0||
187|Randomize Digsites|0|0|Map|
188|Summon and Move Pets|0|0||
189|Unknwon|0|0||
190|Unknown|0|0||
191|Unknown|0|0||
192|Unknown|0|0||
193|Unknown|0|0||
195|Unknown|0|0||
196|Unknown|0|0||
197|Unknown|0|0||
198|Unknown|0|0||
199|Unknown|0|0||
200|Resurect Battle Pets At Percent|0|0||
201|Battle Pet Training|0|0||
202|Unknown (AURA)|1|0||
203|Cast Spell|0|0||
204|Upgrade Battle Pet|0|0||
205|Unknown|0|0||
206|Unknown|0|0||
207|Unknown|0|0||
208|Set Reputation|0|0|Reputation|
209|Unknown|0|0||
210|Learn Garrison Building|0|0|GarrisonBuilding|
211|Unknown|0|0||
213|Unknown|0|0||
214|Unknown|0|0||
215|Unknown|0|0||
216|Create Shpont??|0|0||
217|Unknown|0|0||
218|Unknown|0|0||
219|Unknown|0|0||
220|Obtain Follower|0|0|Follower|
221|Unknown|0|0||
222|Unknown|0|0||
223|Unknown|0|0||
224|Unknown|0|0||
225|Unknown|0|0||
226|Unknown|0|0||
227|Unknown|0|0||
228|Unknown|0|0||
229|Set Follower Quality|0|0||
231|Give Follower Exp|0|0||
232|Unknown|0|0||
233|Retrain Follower|0|0||
235|Unknown|0|0||
236|Gain Exp|0|0||
237|Unknown|0|0||
238|Gain Skill Points|0|0|Skill|
239|Unknown|0|0||
241|Unknown|0|0||
242|Artifact Power (No Scaling)|0|0||
243|Apply Enchant Appearance|0|0|Enchant|
244|Teach Follower Ability|0|0|FollowerAbility|
245|Upgrade Hierloom to level|0|0||
246|Complete Mission|0|0||
247|Unknown|0|0||
248|Unknown|0|0||
249|Gain Artifact Weapon|0|0||
250|Unknown|0|0|Item|
251|Unknown|0|0||
252|Unknown|0|0||
253|Unknown|0|0||
254|Unknown|0|0||
255|Unknown|0|0||Looks like 'LEARN TMOG SET'

---
### Aura Types

This table needs to be fixed up.

Id | Type | Extra
--- | --- | ---
2|Possess|
3|Periodic Damage|
4|Dummy|
5|Confuse|(1)
6|Charm|
7|Fear|
8|Periodic Heal|
9|Mod Attack Speed|
10|Mod Threat|(127)
11|Taunt|
12|Stun|
13|Mod Damage Done|(Physical)
14|Mod Damage Taken|(Physical)
15|Damage shield|
16|Stealth|
17|Stealth Detection|(1)
18|Invisibility|
19|Invisibility Detection|
20|Mod Total Health Regen %|
21|Mod Total Power Regen %|(Mana)
22|Mod Resistance|(Physical)
23|Unknown Effect (Effect #0)|
24|Periodically give power|(Mana)
25|Pacify|
26|Root|
27|Silence|
28|Reflect All Spells|
29|Mod Stat|(Strength)
30|Mod Skill - Temporary|(
31|Increase Run Speed %|
32|Mod Mounted Speed %|
33|Decrease Run Speed %|
34|Increase Max Health - Flat|
35|Increase Max Power - Flat|(Mana)
36|Shapeshift|(Cat Form)
37|Effect Immunity|(Summon Player)
38|State Immunity|(Stunned)
39|Immunity|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
40|Immunity - Damage Only|(All)
41|Immunity - Debuffs Only|(Poison)
42|Proc Trigger Spell|
43|Proc Trigger Damage|
44|Track Creatures|(Critter)
45|Track Resources|(Herbalism)
47|Mod Parry %|
48|Unknown|(Aura #48)
49|Mod Dodge %|
50|Mod Amount Healed by Critical Heals %|(895)
51|Mod Block %|
52|Mod Melee & Ranged Crit %|
53|Periodically Leech Health|
54|Mod Melee & Ranged Hit Chance %|
55|Mod Spell Hit Chance %|
56|Change Model|(
57|Mod Spell Crit %|
58|Increase Swim Speed %|
59|Increase Physical Damage & Spell Damage|(Demon)
60|Pacify & Silence|
61|Mod Size %|
62|Periodically Transfer Health|
63|Unknown|(Aura #63) (4)
64|Periodically Drain Power|(Mana)
65|Mod Spell Haste %|
66|Feign Death|
67|Disarm|
68|Stalked|
69|Absorb Damage|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
70|Unknown|(Aura #70)
71|Mod Spell Crit %|
72|Mod Mana Cost %|(All)
73|Mod Mana Cost %|(Frost)
74|Reflect Spells|(All)
75|Force Language|(Demonic)
76|Far Sight|(15)
77|Immunity - Mechanic|(Polymorphed)
78|Mounted|(
79|Mod Damage Done %|(Physical)
80|Mod Stat %|(All)
81|Split Damage %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
82|Underwater Breathing|
83|Mod Base Resistance Flat|(All)
84|Health Regen|
85|Power Regen|(Mana)
86|Create Item on Death|
87|Mod % Damage Taken|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
88|Mod Health Regen %|
89|Mod Periodic Damage %|
90|Unknown|(Aura #90)
91|Mod Aggro Range|
92|Cannot Flee|
93|Unattackable|
94|Interrupt Power Decay|
95|Ghost|
96|Magnet|
97|Absorb Damage - Mana Shield|(Physical)
98|Mod Skill|(
99|Mod Melee Attack Power|
100|Always Show Debuffs|(Obsolete)
101|Mod Resistance %|(Physical)
102|Mod Melee Attack Power vs Creature|(Demon)
103|Mod Threat Flat - Temporary|
104|Water Walking|
105|Slow Fall|
106|Levitate|/ Hover
107|Modifies Effect|#3's Value (23)
108|Modifies Power Cost|(14)
109|Proc Spell on Target|
110|Mod Power Regen %|(Energy)
111|Intercept % of all Melee & Ranged Attacks|
112|Override Class Script|(911)
114|Mod Ranged Damage Taken - %|(1)
115|Mod Healing Taken - Flat|(All)
116|Allow % of Health Regeneration to Continue in Combat|
117|Give % Chance to Resist Mechanic|(Silenced)
118|Mod Healing Taken - %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
119|Unknown|(Aura #119)
120|Untrackable|
121|Beast Lore|
122|Mod Off-Hand Damage Done %|
123|Reduce Target Resistances - Flat|(Fire)
124|Mod Ranged Attack Power|
125|Mod Melee Damage Taken|
126|Mod Melee Damage Taken - %|
127|Mod Attacker Ranged Attack Power|
128|Take Control of Pet|
129|Increase Run Speed % - Stacks|
130|Incerase Mounted Speed % - Stacks|
131|Mod Ranged Attack Power vs Creature|(Demon)
132|Mod Increase Maximum Power - %|(Mana)
133|Mod Increase Maximum Health - %|
134|Allow % of Mana Regeneration to Continue in Combat|
135|Mod Healing Power|(All)
136|Mod Healing Power - %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
137|Mod Stat - %|(Stamina)
138|Mod Melee Attack Speed - %|
139|Force Reputation|(
140|Mod Ranged Attack Speed - %|
141|Mod Ranged Attack Speed - % - Ammo Only|(1)
142|Mod Base Resistance - %|(Fire)
143|Mod Resistace - Flat - Does not Stack|(Frost, Nature, Shadow)
144|Reduce Falling Damage by %|
145|Increase Pet Talent Points|(1728)
146|Allow Exotic Pets Taming|(1)
147|Add Creature Immunity|(?) (Asleep, Disarmed, Distracted, Snared, Slowed)
148|Add Combo Points for|20 Seconds (1392)
149|Decrease Pushback Time by %|(All)
150|Mod Block Value - %|
151|Track Hidden|
152|Mod Aggro Range of Mobs Against You|
153|Unknown|(Aura #153)
154|Mod Stealth Effectiveness|
155|Underwater Breathing|
156|Mod All Reputation Gained by %|
157|Mod All Pet Damage Taken|
158|Mod Block Value|
159|Worth No Honor|
161|Regen Health - Works in Combat|
162|Power Burn|(Mana)
163|Mod Melee Critical Damage %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
164|Unknown|(Aura #164)
165|Marked by a Guard|
166|Mod Melee Attack Power - %|
167|Mod Ranged Attack Power - %|
168|Mod All Damage Done Against Creature - %|(Demon, Undead)
169|Unknown|(Aura #169)
170|Make a Certain Object Visible|(1)
171|Mod Mounted Speed % - Stacks|
172|Mod Mounted Speed % - Doesn|'t Stack with Anything
173|Unknown|(Aura #173) (1201)
174|Mod Spell Power by % of Stat|(All)
175|Mod Healing Power by % of Stat|(Intellect)
176|Spirit of Redemption|
177|Mind Control|(AoE only?)
178|Mod Debuff Resistance - %|
179|Mod Attacker Crit Chance %|(Holy, Nature, Physical)
180|Mod Spell Power Against Creature|(Undead)
181|Unknown|(Aura #181) (1220)
182|Mod Resistance by % of Stat|(187)
183|Mod Threat % of Critical Hits|
184|Mod Attacker Melee Hit Chance - %|
185|Mod Attacker Ranged Hit Chance - %|
186|Mod Attacker Spell Hit Chance - %|(126)
187|Mod Attacker Melee Crit Chance - %|
188|Mod Attacker Ranged Crit Chance - %|
189|Mod Rating|(
190|Mod Reputation Gained %|(
191|Run Speed Limit %|
192|Increase Attack Speed %|
193|Decrease Attack Speed %|
194|Bypass Damage Reduction Effects|(Nature, Shadow)
196|Increase All Cooldowns|
197|Mod Chance to be Critically Hit %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
198|Unknown|(Aura #198) (256)
199|Mod Spell Hit Chance %|(21)
200|Mod Experience Gained %|(mob kills only)
201|Cannot dodge|, block or parry
203|Mod Melee Crit Damage Taken by %|
204|Mod Ranged Crit Damage Taken by %|
205|Mod Spell Crit Damage Taken by %|(Physical)
206|Mod Flight Speed % - Stacks|
207|Mod Flight Speed %|
208|Mod Flight Speed %|
209|Mod Mounted Speed %|
210|Mod Flight Speed %|
211|Mod Mounted Speed %|(ground + flying)
212|Mod Ranged Attack Power by % of Stat|(1)
213|Mod Rage % Generated From Damage Dealt|
214|Tamed Pet Passive|
215|Arena Preparation|
216|Mod Casting Speed - %|
217|Unknown|(Aura #217)
218|Aura Unknown - %|(3)
219|Mod Mana Regeneration by % of Stat|(7)
220|Mod Combat Rating by % of Stat|(
221|Ignored|
222|Unknown|(Aura #222)
223|Unknown|(Aura #223)
224|Unknown|(Aura #224) (19241)
225|Unknown|(Aura #225) (40)
226|Periodic Dummy|
227|Periodically Trigger Spell with Value|
228|Stealth Detection|(Always)
229|Mod AoE Damage Taken %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
230|Mod Max Health|
231|Unknown|(Aura #231)
232|Mod Mechanic Duration %|(Snared)
233|Change Model of Every Humanoid Seen|(1728)
234|Mod Mechanic Duration % - Does not Stack|(Disarmed)
235|Mod Dispel Resistance %|
236|Control Vehicle|
239|Mod Size % - Doesn|'t stack
240|Mod Expertise|
241|Unknown|(Aura #241)
242|Mod Spell Power & Healing Power by % of Intellect|
243|Faction Override|(2023)
244|Comprehend Language|(Zombie)
245|Mod Debuffs Duration %|(Magic)
247|Clone|(3)
249|Create Death Rune|(Blood)
250|Increase Max Health - Stacks|
251|Mod Enemy Dodge %|
252|Mod Melee|, Ranged & Spell Haste by %
253|Critical Block Chance %|(8)
254|Remove Shield|
255|Mod Mechanic Damage %|(Bleeding)
258|Unknown|(Aura #258) (35591)
259|Mod Periodic Healing Taken %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
260|Screen Effect|(221)
261|Phase|(2)
262|Unknown|(Aura #262) (126)
263|Allows Spells|
264|Unknown|(Aura #264)
267|Cancel Aura if Damage Absorbed Reaches X% of Caster Health|(All)
269|Unknown|(Aura #269) (127)
270|Unknown|(Aura #270) (127)
271|Mod All Damage Done % by Caster|
273|Unknown|(Aura #273) (25532)
275|Allow Affected Spells to be Used in Any Stance|(0)
276|Mod Damage Done % by Mechanic|(Distracted)
278|Disarm Ranged Weapon|
279|Spawn Effect|
280|Mod Armor Penetration %|
281|Mod All Honor Gain %|
283|Mod All Healing Done % by Caster|(49152)
284|Unknown|(Aura #284)
287|Unknown|(Aura #287)
288|Unknown|(Aura #288)
289|Unknown|(Aura #289)
290|Mod Crit Chance % - All|
291|Mod Experience Gained %|(Quests too)
293|Mechanic Abilities|(740)
294|Aura of Despair|(1)
296|Unknown|(Aura #296) (412)
297|Unknown|(Aura #297)
298|Unknown|(Aura #298)
300|Unknown|(Aura #300) (127)
301|Mod Healing Absorb %|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
303|Unknown|(Aura #303) (22)
304|Unknown|(Aura #304) (23697)
305|Mod Minimum Speed %|
308|Mod Critical Strike %|(7)
309|Unknown|(Aura #309) (2)
310|Mod Pet AOE Damage Avoidance|(Arcane, Fire, Frost, Holy, Nature, Physical, Shadow)
311|Unknown|(Aura #311) (926)
312|Animation Replacement|(61)
313|Unknown|(Aura #313) (278)
314|Unknown|(Aura #314) (78)
315|Unknown|(Aura #315)
317|Unknown|(Aura #317) (126)
318|Mod Mastery %|
319|Mod Melee Attack Speed|
321|Unknown|(Aura #321)
322|Unknown|(Aura #322)
323|Unknown|(Aura #323)
326|Unknown|(Aura #326) (17)
327|Unknown|(Aura #327)
328|Unknown|(Aura #328) (10)
329|Unknown|(Aura #329) (6)
330|Allows Cast while Moving|(7)
331|Unknown|(Aura #331) (5)
332|Overrides Actionbar Spell|
333|Overrides Actionbar Spell|
335|Unknown|(Aura #335)
336|Unknown|(Aura #336) (15)
338|Unknown|(Aura #338) (3)
340|Unknown|(Aura #340) (3)
341|Unknown|(Aura #341) (1176)
342|Mod Attack Speed %|
343|Unknown|(Aura #343)
344|Mod Auto Attack Damage %|
345|Ignore Armor %|
346|Unknown|(Aura #346) (24)
349|Mod Currency Gain|(
351|Unknown|(Aura #351) (82)
352|Unknown|(Aura #352)
354|Mod Healing Based on Target Health %|(2)
355|Unknown|(Aura #355)
357|Unknown|(Aura #357) (1)
358|Unknown|(Aura #358)
359|Unknown|(Aura #359) (22)
360|Unknown|(Aura #360)
361|Triggers AoE|
362|Unknown|(Aura #362)
363|Unknown|(Aura #363)
365|Unknown|(Aura #365)
366|Override Spell Power By AP %|
367|Unknown|(Aura #367) (114093)
368|Unknown|(Aura #368)
369|Unknown|(Aura #369) (86)
371|Unknown|(Aura #371)
372|Unknown|(Aura #372) (63042)
373|Mod Speed % and Unable to Control Character|
374|Unknown|(Aura #374) (185)
377|Allows Movement while Casting|
379|Unknown|(Aura #379)
382|Mod Pet Damage %|(1)
383|Unknown|(Aura #383) (11)
388|Unknown|(Aura #388) (392)
393|Unknown|(Aura #393)
394|Unknown|(Aura #394) (1)
395|Area Trigger|(387)
396|Trigger Spell by Power Level|(9)
397|Unknown|(Aura #397) (2)
398|Unknown|(Aura #398) (1)
399|Unknown|(Aura #399)
400|Unknown|(Aura #400) (393)
401|Unknown|(Aura #401) (213766)
402|Unknown|(Aura #402) (202)
403|Unknown|(Aura #403) (31884)
404|Attack Power equals Spell Power %|
405|Mod Secondary Stat %|(
406|Unknown|(Aura #406) (10)
407|Loss of Control|
408|Unknown|(Aura #408)
409|Unknown|(Aura #409)
411|Modifies Charges|(1365)
413|Unknown|(Aura #413)
414|Unknown|(Aura #414) (127)
415|Unknown|(Aura #415)
416|Unknown|(Aura #416)
417|Unknown|(Aura #417) (11)
418|Modifies Max Power - Flat|(Combo Point)
419|Mod Mana Pool %|
420|Unknown|(Aura #420)
421|Unknown|(Aura #421)
422|Unknown|(Aura #422) (127)
426|Unknown|(Aura #426) (960)
427|Unknown|(Aura #427)
428|Unknown|(Aura #428) (4)
429|Mod Pet Damage %|
430|Unknown|(Aura #430) (35)
431|Unknown|(Aura #431) (3)
434|Unknown|(Aura #434)
436|Unknown|(Aura #436)
437|Unknown|(Aura #437)
438|Unknown|(Aura #438)
441|Mod Multistrike Damage %|
443|Mod Leech %|
447|Unknown|(Aura #447) (1)
448|Unknown|(Aura #448)
450|Unknown|(Aura #450)
451|Unknown|(Aura #451)
453|Unknown|(Aura #453) (1536)
454|Unknown|(Aura #454) (1663)
455|Unknown|(Aura #455)
457|Unknown|(Aura #457) (1500)
458|Unknown|(Aura #458)
459|Unknown|(Aura #459)
460|Unknown|(Aura #460)
463|Converts one stat into another %|
465|Unknown|(Aura #465)
466|Unknown|(Aura #466)
467|Unknown|(Aura #467) (3)
468|Unknown|(Aura #468) (1)
469|Unknown|(Aura #469) (1)
470|Unknown|(Aura #470) (174)
471|Mod Versatility %|
472|Unknown|(Aura #472)
473|Unknown|(Aura #473)
474|Unknown|(Aura #474) (57)
475|Unknown|(Aura #475)
476|Unknown|(Aura #476) (823)
477|Unknown|(Aura #477)
479|Unknown|(Aura #479)
480|Unknown|(Aura #480)
482|Unknown|(Aura #482) (120)
483|Unknown|(Aura #483)
484|Unknown|(Aura #484) (179202)
485|Unknown|(Aura #485)
486|Unknown|(Aura #486)
488|Unknown|(Aura #488)
489|Unknown|(Aura #489) (1)
490|Unknown|(Aura #490)
491|Unknown|(Aura #491)


---
### Item Qualities

Id | Type | Color (RGB)
--- | --- | ---
0 | POOR | rgb(157,157,157)
1 | NORMAL | rgb(255,255,255)
2 | UNCOMMON | rgb(30,255,0)
3 | RARE | rgb(0,112,221)
4 | EPIC | rgb(163,53,238)
5 | LEGENDARY | rgb(255,128,0)
6 | ARTIFACT | rgb(230,204,128)
7 | HEIRLOOM | rgb(0,204,255)

---
### Socket Types

Id | Type
--- | ---
0|Meta Gem
1|Red Gem
2|Blue Gem
3|Yellow Gem
4|Purple Gem
5|Sha-Touched Gem
6|Cogwheel Gem
7|Prismatic Gem
8|Iron Artifact Relic
9|Blood Artifact Relic
10|Shadow Artifact Relic
11|Fel Artifact Relic
12|Arcane Artifact Relic
13|Frost Artifact Relic
14|Fire Artifact Relic
15|Water Artifact Relic
16|Life Artifact Relic
17|Storm Artifact Relic
18|Holy Artifact Relic

---
### Effect Triggers

Id | Description
--- | ---
0|On rightclick
1|On equip
2|Chance on hit
4|Always active
6|Item Class Specific Trigger ([List of known here](#effect-trigger-6-extra))

---
### Effect Trigger 6 Extra

Item Class Id | Description
--- | ---
9 (Recipe) | Learn Recipe on use
15 (Mount) | Learn mount on use
Other | On Rightclick run spell.

# Endpoints
## -> Get type by Id
__URL__ `GET /wowdb/{type}/{id}`

Where `type` is one of `item`,`spell`,`mount`,`faction`,`skill`,`title`, or `achievement`

__**Required Account Permissions:** WOWDB__

>Returns: data based on the request type, 400 ID not found/invalid

`type` value | return type
--- | --- 
`item` | [`Item`](#-item)
`spell` | [`Spell`](#-spell)
`mount` | [`Mount`](#-mount)
`faction` | [`Faction`](#-faction)
`skill` | [`Skill`](#-skill)
`title` | [`Title`](#-title)
`achievement` | [`Achievement`](#-achievement)

## -> Search for type with field data
__URL__ `GET /wowdb/search/{type}/{field}/{value}`

Where `type` is one of `item`,`spell`,`mount`,`faction`,`skill`,`title`, or `achievement`

Where `field` is one of a set of options dependant on `type`

__**Required Account Permissions:** WOWDB__

>Returns: Array of data based on type, or empty array if none found.
>
>Up to 10 results will be returned for normal accounts. UPGRADED accounts will get up to 50

`type` value | Possible search fields | Return type 
 --- | --- | ---
`item` |`String` name, `String` description| [`Array<Item>`](#-item)
`spell` |`String` name| [`Array<Spell>`](#-spell)
`mount` |`String` name| [`Array<Mount>`](#-mount)
`faction` |`String` name| [`Array<Faction>`](#-faction)
`skill` |`String` name| [`Array<Skill>`](#-skill)
`title` |`String` name, `String` namefemale| [`Array<Title>`](#-title)
`achievement` |`String` name| [`Array<Achievement>`](#-achievement)

## -> Get icon of type by Id
__URL__ `GET /wowdb/icon/{type}/{id}`

Where `type` is one of `item`,`spell`,`mount`,`skill`, or `achievement`

__**Required Account Permissions:** WOWDB__

>Returns: A PNG image of type's icon, or 400 ID not found/invalid

## -> Get image of type by Id
__URL__ `GET /wowdb/img/{type}/{id}`

Where `type` is `item` or `area`

__**Required Account Permissions:** WOWDB__

>Returns: A PNG mockup of the ingame tooltip

---