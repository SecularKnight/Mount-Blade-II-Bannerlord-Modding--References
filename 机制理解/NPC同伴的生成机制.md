# NPC同伴的生成机制

> [信息来自原帖](https://forums.taleworlds.com/index.php?threads/adding-companions-wanderers-research-and-development.406014/) 帖子还进行了一些机制修改的尝试，我没怎么看懂。
---

### 创建游戏世界时，生成同伴的机制：

- ##### 使用职业“流浪者”获取所有有效的NPC模板。

  > grabs all the valid NPC templates with the occupation 'Wanderer'

  ###### 参考逻辑：

  ```csharp
  // Token: 0x060025A2 RID: 9634
          public void OnNewGameCreated(CampaignGameStarter campaignGameStarter)
          {
              this._companionTemplates = new List<CharacterObject>(from x in CharacterObject.Templates
              where x.Occupation == Occupation.Wanderer
              select x);
              this._nextRandomCompanionSpawnDate = CampaignTime.WeeksFromNow(this._randomCompanionSpawnFrequencyInWeeks);
              this.SpawnUrbanCharacters();
          }
  ```

  （XML文件中有大量未完成/未使用的文件，通过注释掉“ isTemplate = true”将其取消激活）

  >  (there are tons of unfinished/unused ones in the files, deactivated by commenting out "isTemplate=true")

- ##### 生成NPC的逻辑（反编译得出）：

  ```c#
  int count = this._companionTemplates.Count;
  float num5 = MathF.Clamp(25f / (float)count, 0.33f, 1f);
  
  foreach (CharacterObject companionTemplate in this._companionTemplates)
              {
                  if (MBRandom.RandomFloat < num5)
                  {
                      this.CreateCompanion(companionTemplate);
                  }
  ```

它将25除以模板数量，并将结果限制在0.33和1之间，然后遍历每个模板并根据该概率生成它们。 我推断：如果模板少于或少于25个，它们都会生成； 如果存在任意数量的模板，则将生成其中的三分之一。 大概还有其他障碍可以阻止它变得太傻了。

> it divides 25 by the number of templates and clamps the result between 0.33 and 1, then goes through every template and spawns them based on that probability. I infer: if there are 25 or fewer templates, all of them will spawn; if there is an arbitrarily large number of templates, one third of them will spawn. Presumably there are other barriers in place to stop it getting too silly.
>

---

### 游戏进行时，NPC生成相关的一些参数：

```
private float _randomCompanionSpawnFrequencyInWeeks = 6f;
private float _companionSpawnCooldownForSettlementInWeeks = 6f; 
private const float TargetCompanionNumber = 25f;
```

