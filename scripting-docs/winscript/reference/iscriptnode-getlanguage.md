---
title: IScriptNode::GetLanguage | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetLanguage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetLanguage
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 36b7076bf7f261e462802174c6f9014403606ac8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152854"
---
# <a name="iscriptnodegetlanguage"></a>IScriptNode::GetLanguage
Возвращает язык сценариев, используемый узлом текущего скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstr`  
 [out] Возвращает «JScript», если узел скрипта использует JScript или «VBScript», если узел скрипта использует Visual Basic Scripting Edition (VBScript).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)