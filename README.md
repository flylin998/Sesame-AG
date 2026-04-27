把这个模块改成【本地免设备绑定、直接运行】！
整个 ApplicationHook.kt 里，只有这一处是设备绑定 / 设备验证：
if (Detector.isLegitimateEnvironment(appContext!!)) {
    Detector.dangerous(appContext!!)
    return
}

直接注释掉 / 删掉

kotlin
// 下面这一整段 全部注释！！！
// if (Detector.isLegitimateEnvironment(appContext!!)) {
//     Detector.dangerous(appContext!!)
//     return
// }



个必须改的地方（授权验证）
Config.load(userId)
if (!Config.isLoaded()) return false

@Synchronized
private fun initHandler(): Boolean {
    // 直接加在这里！！！
    offline = false
    // 结束
