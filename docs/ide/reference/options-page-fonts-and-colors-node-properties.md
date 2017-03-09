---
title: "Страница &quot;Параметры&quot;, свойства узла &quot;Шрифты и цвета&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Параметры средств, свойства узла "Шрифты и цвета""
  - "автоматизация [Visual Studio], управление параметрами средств"
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Страница &quot;Параметры&quot;, свойства узла &quot;Шрифты и цвета&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В этом документе описываются свойства шрифтов и цветов для окна инструментов, зарегистрированного для отображения в узле **Шрифты и цвета** в категории **Среда** диалогового окна **Параметры**.  Таким образом поддерживается динамическая природа групп цветных элементов, которые могут меняться при установке и удалении пакетов VSPackage.  
  
 В следующем подразделе показан пример зарегистрированного типа окна и свойств, доступных для каждого окна.  
  
## "Текстовый редактор" или "Принтер" или "Диалоговые окна и окна инструментов"  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 \-или\-  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 \-или\-  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Имя элемента свойства|Значение|Описание|  
|---------------------------|--------------|--------------|  
|FontFamily|Get\/Set \(строка\)|Имя используемого шрифта, например "Courier New".|  
|FontCharacterSet|Get\/Set \(<xref:EnvDTE.vsFontCharSet>\)|Значение <xref:EnvDTE.vsFontCharSet>, задающее тип используемой кодировки, например “Иврит” или "Русская".|  
|FontSize|Get\/Set \(Short\)|Размер используемого шрифта в точках.  Например, 10 или 12.|  
  
## См. также  
 [Управление параметрами](../Topic/Controlling%20Options%20Settings.md)   
 [Определение имен элементов свойств на страницах параметров](../Topic/Determining%20the%20Names%20of%20Property%20Items%20on%20Options%20Pages.md)   
 [Страница “Параметры”, свойства узла “Среда”](../../ide/reference/options-page-environment-node-properties.md)   
 [Страница "Параметры"", свойства узла "Текстовый редактор"](../../ide/reference/options-page-text-editor-node-properties.md)