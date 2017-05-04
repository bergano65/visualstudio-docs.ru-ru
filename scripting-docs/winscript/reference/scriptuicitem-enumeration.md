---
title: "Перечисление SCRIPTUICITEM | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Перечисление SCRIPTUICITEM
Представляет тип элемента пользовательского интерфейса.  Используемый в [Метод IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).  
  
## Синтаксис  
  
```vb  
typedef enum tagSCRIPTUICITEM {   
    SCRIPTUICITEM_INPUTBOX = 1,   
    SCRIPTUICITEM_MSGBOX = 2,   
    } SCRIPTUICITEM;  
  
```  
  
## Значения перечисления  
  
|||  
|-|-|  
|SCRIPTUICITEM\_INPUTBOX|Элемент управления вводом.|  
|SCRIPTUICITEM\_MSGBOX|Окно сообщения.|