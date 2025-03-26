## 🧠 **一、常见设计模式识别技巧**

设计模式一般分为三大类：**创建型模式**、**结构型模式**、**行为型模式**。每种模式都有独特的“特征”，掌握这些特征，就能快速定位它属于哪个模式👇：

### 👉 **创建型模式（与对象的创建相关）**

1. **单例模式**
   - **特征**：
       - 只有一个实例
       - 提供一个全局访问点
       - 常见实现：`getInstance()` 方法

2. **工厂模式**
   - **特征**：
       - 提供一个创建对象的接口
       - 子类负责创建具体对象

3. **建造者模式**
   - **特征**：
       - 将对象的创建与表示分离
       - 使用链式调用（`Builder`）

---

### 👉 **结构型模式（处理类或对象的组合）**

1. **适配器模式**
   - **特征**：
       - 将不兼容的接口通过中间类适配

2. **装饰器模式**
   - **特征**：
       - 在不修改原类的情况下动态扩展功能

3. **代理模式**
   - **特征**：
       - 控制对目标对象的访问

---

### 👉 **行为型模式（对类或对象进行交互和分配）**

1. **观察者模式**
2. **策略模式**

3. **命令模式**
   - **特征**：
       - 将操作封装成对象
       - 可以保存、撤销或重做操作
   - **代码示例**：
   ```java
   interface Command {
       void execute();
   }

   class ConcreteCommand implements Command {
       private Receiver receiver;

       ConcreteCommand(Receiver receiver) {
           this.receiver = receiver;
       }

       public void execute() {
           receiver.action();
       }
   }

   class Receiver {
       void action() {
           System.out.println("Executing Command");
       }
   }
   ```
   - **识别技巧**：
      👉 如果看到一个类封装了一个操作，然后能重复执行，就是命令模式。

4. **责任链模式**
   - **特征**：
       - 将请求在连接的处理者中传递
       - 可以按照不同条件分配请求
   - **代码示例**：
   ```java
   abstract class Handler {
       protected Handler next;
       public void setNext(Handler next) { this.next = next; }
       public abstract void handleRequest(int request);
   }

   class ConcreteHandlerA extends Handler {
       public void handleRequest(int request) {
           if (request < 10) {
               System.out.println("HandlerA processed: " + request);
           } else if (next != null) {
               next.handleRequest(request);
           }
       }
   }
   ```
   - **识别技巧**：
      👉 如果看到请求在一系列类中传递，就是责任链模式。

---

## 其他内容不变，详细模式请参考以上内容︌意见欢迎交流︌🚀

