---
title: 'IDebugDocumentHelper:: Сетдефаулттекстаттр | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDefaultTextAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea63f028497f1eb90803f59423f608d0a42960cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574638"
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Задает атрибуты по умолчанию, используемые для текста, который не находится в блоке скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `staTextAttr`  
 Атрибуты текста источника по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Если этот метод не изменяет атрибуты по умолчанию, то для текста за пределами блока скрипта используются атрибуты по умолчанию SOURCETEXT_ATTR_NONSOURCE. Пользовательский интерфейс может использовать эти сведения для пометки текста вне блоков скриптов как предназначенных только для чтения.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)