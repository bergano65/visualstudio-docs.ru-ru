---
title: "Член &quot;Mustoverride&quot;, не совместимый с CLS, нельзя использовать в &lt;имя_класса&gt;, совместимом с CLS. | Microsoft Docs"
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
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член &quot;Mustoverride&quot;, не совместимый с CLS, нельзя использовать в &lt;имя_класса&gt;, совместимом с CLS.
Класс помечен как `<CLSCompliant(True)>`, но содержит процедуру или свойство `MustOverride`, помеченное как `<CLSCompliant(False)>` или не помеченное вообще.  
  
 Если класс совместим с [Независимость от языка и независимые от языка компоненты](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), приложение, использующее этот класс, обращается только к членам, которые также помечены как `<CLSCompliant(True)>`, и игнорирует члены, не помеченные таким образом. Однако приложение не может игнорировать процедуру или свойство `MustOverride`, поскольку доступ к этому объекту необходим для его переопределения.  
  
 При применении атрибута <xref:System.CLSCompliantAttribute> к программному элементу вы задаете для параметра `isCompliant` атрибута значение `True` или `False`, чтобы указать совместимость или несовместимость. Для этого параметра нет значения по умолчанию, и вы должны предоставить его.  
  
 Если вы не применяете <xref:System.CLSCompliantAttribute> к элементу, он считается несовместимым.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC40034  
  
### Исправление ошибки  
  
-   Если требуется совместимость с CLS и вы можете управлять исходным кодом класса, пометьте член как `<CLSCompliant(True)>`.  
  
-   Если требуется совместимость с CLS и вы не можете управлять исходным кодом класса, или он не квалифицирован как совместимый, определите этот член в другом классе.  
  
-   Если требуется, чтобы этот член оставался несовместимым, удалите ключевое слово `MustOverride` из его определения, удалите <xref:System.CLSCompliantAttribute> из определения класса или пометьте этот класс как `<CLSCompliant(False)>`.  
  
## См. также  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [\<PAVE OVER\> Создание кода, совместимого с CLS](http://msdn.microsoft.com/ru-ru/4c705105-69a2-4e5e-b24e-0633bc32c7f3)