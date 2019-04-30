---
title: IDebugDocumentText::GetText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 63e1fee3531272f18c85c23ea83b8ca12920bd2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970865"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Извлекает символы и символ атрибуты, связанные с диапазоном позицию символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 [in] Местоположение символа диапазона позиции начала.  
  
 `pcharText`  
 [in, out] Символ текстового буфера. Размер буфера должен быть достаточно большим, чтобы хранить `cMaxChars` символов. Если этот параметр имеет значение NULL, метод не возвращает символы.  
  
 `pstaTextAttr`  
 [in, out] Атрибут символьный буфер. Размер буфера должен быть достаточно большим, чтобы хранить `cMaxChars` символов. Если этот параметр имеет значение NULL, метод не возвращает атрибуты.  
  
 `pcNumChars`  
 [in, out] Число возвращаемых символов и атрибуты. Этот параметр должен быть установлено в ноль перед вызовом этого метода.  
  
 `cMaxChars`  
 [in] Число символов в диапазоне положение символов. Также указывает максимальное количество возвращаемых символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод извлекает символы и символ атрибуты, связанные с диапазоном позицию символа. Позиция диапазона знаков задается позицию символа и число символов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)