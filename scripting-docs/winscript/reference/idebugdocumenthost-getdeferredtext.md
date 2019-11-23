---
title: 'IDebugDocumentHost:: Жетдеферредтекст | Документация Майкрософт'
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
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569426"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Возвращает диапазон символов, добавленных с помощью метода `IDebugDocumentHelper::AddDeferredText` в исходном документе размещения.  
  
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
 окне Определяемый узлом файл cookie, представляющий начальную точку текста.  
  
 `pcharText`  
 [вход, выход] Символьный текстовый буфер. Этот метод не возвращает символы, если этот параметр имеет значение `NULL`.  
  
 `pstaTextAttr`  
 [вход, выход] Буфер символьного атрибута. Этот метод не возвращает атрибуты, если этот параметр имеет значение `NULL`.  
  
 `pcNumChars`  
 [вход, выход] Указывает фактическое число возвращаемых символов и атрибутов. Перед вызовом этого метода этот параметр должен быть установлен в ноль.  
  
 `cMaxChars`  
 окне Максимальное число возвращаемых символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Метод не реализован.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод может возвращать `E_NOTIMPL`, если узел не вызывает `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
> Этот метод возвращает текст из исходного документа. Узел не отслеживает изменения и другие изменения в документе.  
  
## <a name="see-also"></a>См. также:  
   [интерфейса IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
 [IDebugDocumentHelper:: адддеферредтекст](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Перечисление SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)