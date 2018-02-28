---
title: "IDebugDocumentHelper::SetDefaultTextAttr | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49b6da490e1eefe13ae21a9875952032585372f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Задает атрибуты по умолчанию, используемый для текста, не находящийся в блок сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `staTextAttr`  
 Атрибуты по умолчанию исходного текста.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Первоначально атрибуты по умолчанию с помощью данного метода по умолчанию атрибутов текста за пределами блока скрипта является SOURCETEXT_ATTR_NONSOURCE. Пользовательский интерфейс можно использовать эту информацию для выделения текста за пределами блоков сценариев только для чтения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)