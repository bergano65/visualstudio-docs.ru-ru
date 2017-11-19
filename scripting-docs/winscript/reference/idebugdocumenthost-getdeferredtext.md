---
title: "IDebugDocumentHost::GetDeferredText | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Возвращает диапазон символов, которые были добавлены с помощью `IDebugDocumentHelper::AddDeferredText` метод в исходном документе узла.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Определить на уровне узла куки-файл, представляющий начальное положение текста.  
  
 `pcharText`  
 [in, out] Текстовый буфер символов. Этот метод не возвращает символы, если этот параметр является `NULL`.  
  
 `pstaTextAttr`  
 [in, out] Атрибут буфер символов. Этот метод не возвращает атрибуты, если этот параметр равен `NULL`.  
  
 `pcNumChars`  
 [in, out] Указывает фактическое число возвращаемых символов и атрибутов. Этот параметр необходимо устанавливать до нуля перед вызовом этого метода.  
  
 `cMaxChars`  
 [in] Максимальное число возвращаемых символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод может возвращать `E_NOTIMPL`, если узел не был вызван `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Этот метод возвращает текст из исходного документа. Узел не хранить список изменений или других изменений в документ.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)