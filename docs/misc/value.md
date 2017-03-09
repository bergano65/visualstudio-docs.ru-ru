---
title: "__value | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__value - ключевое слово"
  - "типы значений, объявление"
  - "__value-ключевое слово, синтаксис"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  Этот раздел относится только к управляемым расширениям для C\+\+ версии 1. Приведенный здесь синтаксис должен использоваться только для обслуживания кода версия 1. В разделе [Классы и структуры](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) сведения об использовании эквивалентную функциональность в новом синтаксисе.  
  
 Объявляет класс как класс типа \_\_value.  
  
## Синтаксис  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## Заметки  
 Тип `__value` отличается от типов `__gc` в том, что переменные типа `__value` непосредственно содержат собственные данные, в то время как управляемые переменные указывают на свои данные, которые хранятся в куче среды CLR.  
  
 К типам `__value` применяются следующие условия.  
  
-   Ключевое слово `__value` не может применяться к интерфейсу.  
  
-   Тип `__value` может наследоваться от любого числа интерфейсов и не может наследоваться от других типов или типов `__value`.  
  
-   Тип `__value` является запечатанным по определению. Дополнительные сведения см. в разделе [\_\_sealed](../misc/sealed.md).  
  
-   Тип `__value` можно использовать везде, где разрешен управляемый тип.  
  
> [!NOTE]
>  Не разрешается использовать ключевое слово `__value` с ключевым словом `__abstract`.  
  
 Тип `__value` можно явно подключить к указателю **System::Object**. Это называется упаковкой\-преобразованием.  
  
 При внедрении типа значения внутри типа `__nogc` применяются следующие правила.  
  
-   Тип значения должен быть **LayoutSequential** или **LayoutExplicit**.  
  
-   Тип значения не может иметь члены указателя gc.  
  
-   Тип значения не может иметь закрытые данные\-члены.  
  
 В управляемых расширениях для C\+\+ используются следующие эквиваленты класса C\# и структуры C\#.  
  
|Управляемые расширения для C\+\+|C\#|Дополнительные сведения|  
|--------------------------------------|---------|-----------------------------|  
|Структура \_\_gc<br /><br /> \-или\-<br /><br /> Класс \_\_gc|класс|ключевое слово [class](/dotnet/csharp/language-reference/keywords/class)|  
|Структура \_\_value<br /><br /> \-или\-<br /><br /> Класс \_\_value|struct|ключевое слово [struct](/dotnet/csharp/language-reference/keywords/struct)|  
  
## Пример  
 В следующем примере объявляется тип `__value` \(`V`\), а затем выполняются действия с двумя экземплярами типа `__value`.  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```