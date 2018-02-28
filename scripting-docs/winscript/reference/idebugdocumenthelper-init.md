---
title: "IDebugDocumentHelper::Init | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.Init
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Init
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45cd57e4ba9e86bf84f927f487c637d61aa5339b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init` Метод инициализирует помощник отладки документа с именем и исходные атрибуты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pda`  
 [in] Приложение отладки, связанные с данным документом.  
  
 `pszShortName`  
 [in] Нулем строка, содержащая короткое имя файла.  
  
 `pszLongName`  
 [in] Нулем строка, содержащая длинное имя документа.  
  
 `docAttr`  
 [in] Задает атрибуты текста документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод инициализирует помощник отладки документа с именем и исходные атрибуты.  
  
 В этом документе не отображается в дереве до `IDebugDocumentHelper::Attach` вызывается.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Константы TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)