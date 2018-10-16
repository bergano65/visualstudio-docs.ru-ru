---
title: Свойство SCRIPTPROP_HOSTKEEPALIVE | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734144"
---
# <a name="scriptprophostkeepalive-property"></a>Свойство SCRIPTPROP_HOSTKEEPALIVE
Используется для указания ли обработчик скриптов должны храниться полнофункциональными, если нет ожидающих ссылок.  
  
 Используйте [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) задать это свойство `true`. Если это свойство имеет значение `true`, хранится полнофункциональным обработчика скриптов при условии, что имеется по крайней мере один необработанных ссылка для самого обработчика скриптов или `IDispatch` указатель на объект JavaScript, созданные с помощью скрипта модуль. Если значение этого свойства `true`, следует явно не закрывать или сбросить обработчик сценариев с помощью [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) или [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) методы. В выпуске последняя ссылка на объект скрипта обработчик скриптов завершает работу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Требования  
 Это свойство появляется только в версии activscp.idl, которая устанавливается с [!INCLUDE[win8](../../javascript/includes/win8-md.md)], с 2707082 КБ для Internet Explorer 8 на [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], или с 2722913 КБ для Internet Explorer 9 на [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] или [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].