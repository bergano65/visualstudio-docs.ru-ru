---
title: "Корневое пространство имен &lt;имя_пространства_имен&gt; не совместимо с CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40038"
  - "vbc40038"
helpviewer_keywords: 
  - "BC40038"
ms.assetid: ec850295-b2fe-4f19-b808-d22fe0aaa32d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Корневое пространство имен &lt;имя_пространства_имен&gt; не совместимо с CLS
Сборка помечена как `<CLSCompliant(True)>`, но корневое пространство имен начинается со знака подчеркивания \(`_`\).  
  
 Программный элемент может содержать один или несколько символов подчеркивания, но чтобы быть совместимым с [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), он не должен начинаться с символа подчеркивания. См. раздел [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False`, чтобы указать совместимость или несовместимость. Для этого параметра нет значения по умолчанию, и вы должны предоставить его.  
  
 Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40038  
  
### Исправление ошибки  
  
-   Если требуется CLS\-совместимость, измените имя корневого пространства имен, чтобы оно не начиналось с символа подчеркивания.  
  
-   Если требуется, чтобы корневое пространство имен осталось неизменным, удалите <xref:System.CLSCompliantAttribute> из сборки или пометьте его как `<CLSCompliant(False)>`.  
  
## См. также  
 [Оператор Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Пространства имен в Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces)   
 [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)   
 [NIB. Практическое руководство. Изменение пространства имен для приложения \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/029d85c0-e173-4f7a-afba-a29f3aaf6ebf)   
 [Имена объявленных элементов](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Соглашения об именах Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [\<PAVE OVER\> Создание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3)