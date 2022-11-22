# Design Pattern

## OOD Principle
Seven Deadly Sins of Software Design
1. Rigidity (僵化) – make it hard to change
2. Fragility (脆弱) – make it easy to break
3. Immobility (固化) – make it hard to reuse
4. Viscosity (黏滞) – make it hard to do the right thing
5. Needless Complexity (非必要复杂性) – over design
6. Needless Repetition (非必要重复) – error prone
7. Not doing any design

The Principles Of Object Oriented Design
* SRP: Single Responsibility Principle 单一职责原则
    A class should have one reason to change
    Single Responsibility = Increased Cohesion(内聚)
    Multiple Responsibilities = Increased Coupling (耦合)
        Harmful for reusing;
        Changing one responsibility will effect the others,the class is friable for changes.
* OCP: Open-Closed Principle 开放-封闭原则
    Open For Extension: Satisfying the new requirements by adding new modules. 开放扩展
    Closed For Modification: No need and can not modify current modules for new requirements. 封闭修改
* LSP: Liskov Substitution Principle 里氏替换原则
    Any subclass should always be usable instead of its parent class. 任何基类可以出现的地方，子类一定可以出现
    IS A = same public behavior 当一个子类的实例应该能够替换任何其超类的实例时，它们之间才具有is-A关系
    
* ISP: Interface Segregation Principle 接口分离原则
    接口也要单一职责！要瘦不要肥！
    Fat interface is interface pollution;
    Saving the number of interfaces can not reduce the code-amount, but pollute the interfaces.
    Interface should be thin, it is also reasonable even there is no method defined in a interface.
    ISP is SRP in interface version
* DIP: Dependence Inversion Principle 依赖倒置原则
    Higher layer modules should NOT depend on lower layer modules, both should depend on abstractions(interfaces or abstract classes).
    Abstractions should NOT depend on details, details should depend on abstractions

    Any variables should NOT hold a reference which refer to a concrete class, but a interface or abstract class;
    Any classes should NOT inherit from a concrete class;
    Any methods should NOT override the basemethods which has been implemented in base class.
    The rules of DIP is over-strict
    Interface should be defined by the service requester, not services provider
SOLID
* CRP: Composite/Aggregate Reuse Principle 组合/聚合复用原则
    多用组合少用继承！
    在一个新的对象里面使用一些已有的对象， 使之成为新对象的一部分； 新的对象通过向这些对象的委派达到复用已有功能的目的。
* PLK: Principle of Least Knowledge 最小知识原则/Demeter原则
  不要让太多类耦合在一起！易于修改，使修改造成的改动尽可能的小

## Design Pattern
### Observer
Applicability
    When an abstraction has two aspects, one dependent on the other. Encapsulating these aspects in separate objects lets you vary and reuse them independently.

    When a change to one object requires changing others, and you don't know how many objects need to be changed.

    When an object should be able to notify other objects without making assumptions about who these objects are. In other words, you don't want these objects tightly coupled.

Advantages
Minimal coupling between the Subject and the Observer
Support for event broadcasting

额外补充：Push和Pull
Pull model, Observer自己找什么变了,复用性强
Push model, Subject把改变的部分打包发出，复用性差