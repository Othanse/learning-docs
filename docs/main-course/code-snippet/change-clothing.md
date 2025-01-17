# 换装区

## 物体结构

![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcn5qAiTixiQzQEcpk6OVt4xH.png)

## 物体效果

![](https://wstatic-a1.233leyuan.com/productdocs/static/boxcnX0BECihuJ7knZ0UoVC9vEc.gif)

## 代码示例

```ts
@Core.Class
export default class TriggerControl extends Core.Script {

    /** 当脚本被实例后，会在第一帧更新前调用此函数 */
    protected async onStart() {
        //服务端不做任何事
        if(Gameplay.isServer()){
            return
        }
        //以下为客户端逻辑
        //获取当前客户端玩家
        let player = await Gameplay.asyncGetCurrentPlayer()
        //获取当前脚本所挂载的触发器
        let trigger = this.gameObject as Gameplay.Trigger
        //进入触发区域
        trigger.onEnter.add(()=>{
            //角色加载捏人数据，捏人数据请看：https://learning.ark.online/main-course/programming-scripting/character-editor.html
            player.character.loadSlotAndEditorDataByGuid("2FC9B86748B6300CE0B299936B45E1A2")
        })
    }
}
```
