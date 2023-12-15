// 气源管道接口
interface PipeJoint {
    void connectPipe();
}

// 电池接口
interface Battery {
    void replaceBattery();
}

// 油箱接口
interface OilTank {
    void refuel();
}

// 干电池
class DryBatterytocar implements Battery {
    @Override
    public void replaceBattery() {
        System.out.println("汽车不能使用该电池");
    }
}

// 蓄电池
class StorageBatterytocar implements Battery {
    @Override
    public void replaceBattery() {
        System.out.println("汽车可以使用蓄电池");
    }
}
class DryBatterytocooker implements Battery {
    @Override
    public void replaceBattery() {
        System.out.println("燃气灶可用干电池");
    }
}
class StorageBatterytocooker implements Battery {
    @Override
    public void replaceBattery() {
        System.out.println("燃气灶不能使用该电池");
    }
}
class Gasoline implements OilTank{
    public void refuel(){
        System.out.println("加油中...");
    }
}
class Dieseloil implements OilTank{
    public void refuel(){
        System.out.println("不能加柴油");
    }
}
class NaturalGas4mm implements PipeJoint{
    public void connectPipe(){
        System.out.println("燃气接头已连接气源管道");
    }
}
class NaturalGas6mm  implements PipeJoint{
    public void connectPipe(){
        System.out.println("燃气管直径不一致");
    }
}
class LiquefiedGas4mm  implements PipeJoint{
    public void connectPipe(){
        System.out.println("燃气类型不符合");
    }
}
class LiquefiedGas6mm  implements PipeJoint{
    public void connectPipe(){
        System.out.println("燃气类型与燃气管直径均不符合");
    }
}

//燃气灶
class GasCooker implements Battery,PipeJoint {
    private Battery battery;
    private PipeJoint pipejoint;

    public GasCooker(Battery battery ,PipeJoint pipejoint){
        this.battery = battery;
        this.pipejoint = pipejoint;
    }
    @Override
    public void replaceBattery() {
        battery.replaceBattery();
    }
    public void connectPipe(){
        pipejoint.connectPipe();
    }
}
// 小汽车
class Car implements Battery, OilTank {
    private Battery battery;
    private OilTank oilTank;

    public Car(Battery battery, OilTank oilTank) {
        this.battery = battery;
        this.oilTank = oilTank;
    }

    @Override
    public void replaceBattery() {
        battery.replaceBattery();
    }
    public void refuel(){
        oilTank.refuel();
    }
}

// 主类
public class Main {
    public static void main(String[] args) {
        testBattery();
        testPipe();
        testrefuel();
    }

    // 测试电池替换
    public static void testBattery() {
        System.out.println("正在测试汽车与燃气灶换电池...");
        // 创建汽车的干电池和蓄电池
        DryBatterytocar dryBattery1 = new DryBatterytocar();
        StorageBatterytocar storageBattery1 = new StorageBatterytocar();
        // 替换小汽车的电池
        Car car1 = new Car(dryBattery1, null);
        car1.replaceBattery();
        Car car2 = new Car(storageBattery1, null);
        car2.replaceBattery();

        //创造燃气灶的干电池和蓄电池
        DryBatterytocooker dryBattery2 = new DryBatterytocooker();
        StorageBatterytocooker storageBattery2 = new StorageBatterytocooker();
        // 替换燃气灶的电池
        GasCooker gascooker1 = new GasCooker(dryBattery2, null);
        gascooker1.replaceBattery();
        GasCooker gascooker2 = new GasCooker(storageBattery2, null);
        gascooker2.replaceBattery();
    }

    // 测试气源管道连接
    public static void testPipe() {
        System.out.println("正在测试燃气灶连接气源管道...");
        //创建燃气管道的直径以及输送类型
        NaturalGas4mm naturalGas4mm = new NaturalGas4mm();
        NaturalGas6mm naturalGas6mm = new NaturalGas6mm();
        LiquefiedGas4mm liquefiedGas4mm = new LiquefiedGas4mm();
        LiquefiedGas6mm liquefiedGas6mm = new LiquefiedGas6mm();
        // 替换燃气灶的电池
        GasCooker gascooker1 = new GasCooker(null, naturalGas4mm);
        gascooker1.connectPipe();
        GasCooker gascooker2 = new GasCooker(null, naturalGas6mm);
        gascooker2.connectPipe();
        GasCooker gascooker3 = new GasCooker(null, liquefiedGas4mm );
        gascooker3.connectPipe();
        GasCooker gascooker4 = new GasCooker(null, liquefiedGas6mm );
        gascooker4.connectPipe();
    }
    //测试汽车加油
    public static void testrefuel(){
        System.out.println("正在测试汽车加油...");
        //创建汽油类型
        Gasoline gasoline = new Gasoline();
        Dieseloil diesloil = new Dieseloil();
        //为小汽车加油
        Car car1 = new Car(null,gasoline);
        Car car2 = new Car(null,diesloil);
        car1.refuel();
        car2.refuel();
    }
}
