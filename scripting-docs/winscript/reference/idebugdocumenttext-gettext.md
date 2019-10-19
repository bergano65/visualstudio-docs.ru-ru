---
title: 'Идебугдокументтекст:: GetText | Документация Майкрософт'
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
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572082"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Извлекает символы и (или) атрибуты символов, связанные с диапазоном символьной позиции.  
  
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
 окне Начальное расположение диапазона символов.  
  
 `pcharText`  
 [вход, выход] Символьный текстовый буфер. Буфер должен быть достаточно большим, чтобы вместить `cMaxChars` символов. Если этот параметр имеет значение NULL, метод не возвращает символы.  
  
 `pstaTextAttr`  
 [вход, выход] Буфер символьного атрибута. Буфер должен быть достаточно большим, чтобы вместить `cMaxChars` символов. Если этот параметр имеет значение NULL, метод не возвращает атрибуты.  
  
 `pcNumChars`  
 [вход, выход] Число возвращаемых символов и атрибутов. Перед вызовом этого метода этот параметр должен быть установлен в ноль.  
  
 `cMaxChars`  
 окне Число символов в диапазоне позиции символа. Также указывает максимальное число возвращаемых символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод извлекает символы и (или) атрибуты символов, связанные с диапазоном символьной позиции. Диапазон позиции символа определяется символом-положением и числом символов.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугдокументтекст](../../winscript/reference/idebugdocumenttext-interface.md)  
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)