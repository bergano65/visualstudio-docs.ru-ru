---
title: "Тип &quot;&lt;имя_типа1&gt;&quot; невозможно пометить как совместимый с CLS, так как содержащий его тип &quot;&lt;имя_типа2&gt;&quot; не совместим с CLS | Microsoft Docs"
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
  - "vbc40030"
  - "bc40030"
helpviewer_keywords: 
  - "BC40030"
ms.assetid: f1cfcf04-2a99-46ef-ac87-34cc2099125c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа1&gt;&quot; невозможно пометить как совместимый с CLS, так как содержащий его тип &quot;&lt;имя_типа2&gt;&quot; не совместим с CLS
Класс или интерфейс помечен как `<CLSCompliant(True)>`, но при этом вложен в тип, помеченный как `<CLSCompliant(False)>` или не помеченный совсем.  
  
 Чтобы класс или интерфейс был совместим с [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), вся его иерархия вложений должна быть совместимой. Это означает, что каждый тип, в который он вложен, должен быть совместимым.  
  
 При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False`, чтобы указать совместимость или несовместимость. Для этого параметра нет значения по умолчанию, и вы должны предоставить его.  
  
 Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40030  
  
### Исправление ошибки  
  
-   Если требуется совместимость с CLS, определите этот тип в другой иерархии вложений.  
  
-   Если требуется, чтобы этот тип оставался в текущей иерархии вложений, удалите <xref:System.CLSCompliantAttribute> из его определения или пометьте его как `<CLSCompliant(False)>`.  
  
## См. также  
 [\<PAVE OVER\> Создание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3)