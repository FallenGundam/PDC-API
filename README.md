# PDC-API
  __PersistentDataContainer: 可為 物品、實體、方塊 ... 添加自定義標籤的新型儲存方式  
  可以把它看作spigot官方推薦使用的customNBT  
  設置後該數據就會寫入該對象的資料中，該對象如果刪除此標籤也會消失  
  靠慮到skript能使用到的數據類型有限，我編寫的api只提供 String , Number , Boolean 等儲存方式  
  但以我個人來說也很夠用了，如有需要其他方式可自己將數據轉換為字串__  
# Required plugins:
    spigot or paper : 1.14 ~  
    skript : 2.6
    skript-reflect
# API:  
 * ### Expression:
    #### Single Value
    > __Type: String, number(double), boolean__  
    ```
    (PersistentData|PDC) [single]value (key|tag) %string% of %object%
    use Methond: get, set, delete
    Example:
        set PDC value key "damage" of player to 10
        set PDC value key "status-poison" of player to true
        if PDC value key "status-poison" of player is true:
        set {_dmg} to PDC value key "damage" of player
        delete PDC value key "damage" of player
    ```
    #### Multiple Value
    > __Type: String, number(double)__  
    ```
    (PersistentData|PDC) (Array|list) (key|tag) %string% of %object%
    use Methond: get, set, add, remove, delete
    Example:
        set {_effect::*} to "slow" , "curse" and "fire"
        set PDC Array key "effect_list" of player to {_effect::*}
        add "poison" to PDC Array key "effect_list" of player
        set {_playereffect::*} to PDC Array key "effect_list" of player
        remove "slow" from PDC Array key "effect_list" of player
        delete PDC Array key "effect_list" of player
    ```
    #### get All keys from object
    ```
    all (key|tag)[s] in (PersistentData|PDC) of %object%
    use Methond: get, delete
    Example:
        set {_all::*} to all keys in PDC of player
        send "%{_all::*}%"
        delete all keys in PDC of player  #it will clear all PDC value from object
    ```
