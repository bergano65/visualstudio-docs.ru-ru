---
title: IDebugDocumentHost::GetScriptTextAttributes | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a5e56468e51f6d90e37e90c885b6b9df48d5f6e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159001"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Возвращает атрибуты текста для блока текста документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrCode`  
 [in] Текст блока скрипта. Эта строка не заканчивается на null.  
  
 `uNumCodeChars`  
 [in] Число символов в тексте блока скрипта.  
  
 `pstrDelimiter`  
 [in] Адрес-объекта блок сценариев end разделитель. Когда `pstrCode` анализируется из потока текста узел обычно использует разделитель, например две одинарные кавычки («), чтобы обнаружить завершение блока скрипта. Этот параметр задает разделитель, используемый узлом, позволяя обработчик скриптов для предоставления некоторых условного примитивных предварительной обработки (например, замените одинарной кавычки ['] две одинарные кавычки для использования в качестве разделителя). Точный способ (и нужно ли) сценариев подсистемой, эта информация зависит от обработчика скриптов. Установите этот параметр в значение NULL, если узел не используется разделитель для обозначения конца блока скрипта.  
  
 `dwFlags`  
 [in] Флаги, связанные с блоком скрипта. Может представлять собой сочетание этих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Указывает, что идентификаторы и точка операторы должны идентифицироваться с флагами SOURCETEXT_ATTR_IDENTIFIER и SOURCETEXT_ATTR_MEMBERLOOKUP, соответственно.|  
|GETATTRFLAG_THIS|0x0100|Указывает, что идентификатор для текущего объекта должна определяться с флагом SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Указывает, что строка содержимого и текст примечания должны определяться с флагом SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Буфер должен содержать возвращаемые атрибуты.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Узел использует только атрибуты по умолчанию.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает атрибуты текста для произвольный блок текста документа. Это допустимо для узлов вернуть `E_NOTIMPL`, в этом случае используются атрибуты по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)