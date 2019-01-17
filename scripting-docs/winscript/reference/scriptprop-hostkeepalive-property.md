---
title: Свойство SCRIPTPROP_HOSTKEEPALIVE | Документация Майкрософт
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
ms.openlocfilehash: 0c8918e277fa9c7183e6d46a4853824a74fa4548
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346843"
---
# <a name="scriptprophostkeepalive-property"></a>Свойство SCRIPTPROP_HOSTKEEPALIVE
Используется для указания ли обработчик скриптов должен сохраняться полнофункциональный, при наличии ссылки на медиафайл.  
  
 Используйте [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) к этому свойству значение `true`. Если это свойство имеет значение `true`, обработчик сценариев хранится полнофункциональный до тех пор, пока по крайней мере один необработанных ссылки на обработчик скриптов себя или для `IDispatch` указатель на объект JavaScript, созданный с помощью сценариев модуль. Если присвоить этому свойству `true`, следует явно не закрыть или выполнить сброс обработчика сценариев с помощью [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) или [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) методы. В выпуске последняя ссылка на объект скрипта обработчик скриптов завершает работу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Требования  
 Это свойство появляется только в версии activscp.idl, которая устанавливается вместе с [!INCLUDE[win8](../../javascript/includes/win8-md.md)], с помощью 2707082 КБ для Internet Explorer 8 на [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], или с 2722913 КБ для Internet Explorer 9 на [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] или [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].