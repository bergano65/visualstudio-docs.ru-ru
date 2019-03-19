---
title: IDebugDocumentHelper::Init | Документация Майкрософт
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
ms.openlocfilehash: 3b399f51fc042aa1ed297ab30a7bf2c9bc4befca
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160018"
---
# <a name="idebugdocumenthelperinit"></a>IDebugDocumentHelper::Init
`Init` Метод инициализирует вспомогательный объект документа отладки с именем и начальными атрибутами.  
  
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
 [in] Приложение отладки, связанных с этим документом.  
  
 `pszShortName`  
 [in] Завершающаяся нулем строка, содержащая короткое имя документа.  
  
 `pszLongName`  
 [in] Завершающаяся нулем строка, содержащая длинное имя документа.  
  
 `docAttr`  
 [in] Указывает атрибуты текста документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод инициализирует вспомогательный объект документа отладки с именем и начальными атрибутами.  
  
 В этом документе не отображается в дереве до `IDebugDocumentHelper::Attach` вызывается.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Константы TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)