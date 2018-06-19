---
title: IDebugDocumentText::GetText | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728084"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Извлекает символы и символ атрибуты, связанные с диапазоном позиции символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cCharacterPosition`  
 [in] Запустите расположение позиции диапазона знаков.  
  
 `pcharText`  
 [in, out] Текстовый буфер символов. Размер буфера должен быть достаточно велик для хранения `cMaxChars` символов. Если этот параметр имеет значение NULL, метод не возвращает символы.  
  
 `pstaTextAttr`  
 [in, out] Атрибут буфер символов. Размер буфера должен быть достаточно велик для хранения `cMaxChars` символов. Если этот параметр имеет значение NULL, метод не возвращает атрибуты.  
  
 `pcNumChars`  
 [in, out] Число возвращаемых символов и атрибутов. Этот параметр необходимо устанавливать до нуля перед вызовом этого метода.  
  
 `cMaxChars`  
 [in] Число символов в позиции диапазона символов. Также указывает максимальное количество возвращаемых символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод извлекает символы и символ атрибуты, связанные с диапазоном позиции символа. Позиция диапазона символов определяется позиции символа и число символов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)