---
title: 'IDebugDocumentHelper:: init | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e6379052707aa44c0fa52f4cb30db2c4c4fa99
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576866"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
Метод `Init` инициализирует вспомогательный объект документа отладки с именем и исходными атрибутами.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pda`  
 окне Приложение отладки, связанное с этим документом.  
  
 `pszShortName`  
 окне Строка, заканчивающаяся нулем и содержащая краткое имя документа.  
  
 `pszLongName`  
 окне Строка, заканчивающаяся нулем и содержащая длинное имя документа.  
  
 `docAttr`  
 окне Задает атрибуты текстового документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод инициализирует вспомогательный объект документа отладки с именем и исходными атрибутами.  
  
 Этот документ не отображается в дереве до тех пор, пока не будет вызван `IDebugDocumentHelper::Attach`.  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentHelper:: Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
   [интерфейса IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Константы TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)