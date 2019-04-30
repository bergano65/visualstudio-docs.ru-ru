---
title: IDebugDocumentHost::GetDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e5800a6de15d2d59208022fa44d3c2f4c931e14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446573"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Возвращает диапазон символов, которые были добавлены с помощью `IDebugDocumentHelper::AddDeferredText` метода в исходном документе узла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwTextStartCookie`  
 [in] Определяемые узла файл cookie, представляющий начальное положение текста.  
  
 `pcharText`  
 [in, out] Символ текстового буфера. Этот метод не возвращает символы, если этот параметр имеет `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Атрибут символьный буфер. Этот метод не возвращает атрибуты, если этот параметр имеет `NULL`.  
  
 `pcNumChars`  
 [in, out] Указывает фактическое количество возвращаемых символов и атрибуты. Этот параметр должен быть установлено в ноль перед вызовом этого метода.  
  
 `cMaxChars`  
 [in] Максимальное количество возвращаемых символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод может возвращать `E_NOTIMPL`, если узел не вызывает `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Этот метод возвращает текст из исходного документа. Узел не хранить список изменений, или другие изменения в документе.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)