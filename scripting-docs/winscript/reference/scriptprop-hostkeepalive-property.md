---
title: "Свойство SCRIPTPROP_HOSTKEEPALIVE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Свойство SCRIPTPROP_HOSTKEEPALIVE
Используется для определения, должен ли обработчик скриптов, будет находиться полностью функциональную \- если незавершенных ссылки.  
  
 Используйте [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md), чтобы присвоить этому свойству значение `true`.  Если это свойство имеет значение `true`, то обработчик скриптов будет находиться полностью функциональным \- если хотя бы одна выдающая или ссылка на обработчик скриптов, или к указателю `IDispatch` на объект JavaScript, созданный с помощью обработчика скриптов.  Если это свойство имеет значение `true`, нет необходимости явно закрыть или сбросить обработчик скриптов с помощью методов [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) или [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md).  Выпуск последней ссылки на объект скрипта закрывает обработчик скриптов вниз.  
  
## Синтаксис  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## Требования  
 Это свойство отображается только в версии activscp.idl, задается с помощью [!INCLUDE[win8](../../javascript/includes/win8-md.md)], с 2707082 КБ для Internet Explorer 8 в [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], или с 2722913 КБ для Internet Explorer 9 в [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] или [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].