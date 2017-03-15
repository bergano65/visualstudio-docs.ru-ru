---
title: "Microsoft.VisualBasic.ComClassAttribute для класса &quot;&lt;имя_класса&gt;&quot; неявно объявляет &lt;тип&gt; &quot;&lt;имя_члена&gt;&quot;, которое вступает в противоречие с членом, имеющим такое же имя &lt;тип&gt; &quot;&lt;имя_типа&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BC42101"
ms.assetid: 001c8eaa-19b6-44fa-8056-4186ecffbda8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Microsoft.VisualBasic.ComClassAttribute для класса &quot;&lt;имя_класса&gt;&quot; неявно объявляет &lt;тип&gt; &quot;&lt;имя_члена&gt;&quot;, которое вступает в противоречие с членом, имеющим такое же имя &lt;тип&gt; &quot;&lt;имя_типа&gt;&quot;
Microsoft.VisualBasic.ComClassAttribute для класса "\<имя\_класса\>" неявно объявляет \<тип\> "\<имя\_члена\>", который вступает в противоречие с членом из \<тип\> "\<имя\_типа\>", имеющим такое же имя. Используйте команду Microsoft.VisualBasic.ComClassAttribute\(InterfaceShadows:\=True\), если вы хотите скрыть имя для базового типа "\<имя\_типа\>".  
  
 Класс, использующий блок атрибутов `COMClassAttribute`, неявно определяет интерфейс с тем же именем, что и член базового класса. В этом случае имя интерфейса должно скрывать член базового класса.  
  
 По умолчанию данное сообщение является предупреждением. Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC42101  
  
### Исправление ошибки  
  
1.  Если требуется скрыть член базового класса, задайте `InterfaceShadows:=True` в блоке атрибутов `ComClassAttribute`.  
  
2.  Если не требуется скрывать член базового класса, измените имя класса.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Класс ComClassAttribute](http://msdn.microsoft.com/ru-ru/5c2f0835-9210-47dc-bc59-5c1769953574)   
 [Свойство ComClassAttribute.InterfaceShadows](http://msdn.microsoft.com/ru-ru/0fae25bd-e0ba-4755-a76c-3b526b1ac795)