---
title: IDebugDocumentHelper::Init | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d4bcb64b7bbb1c61e7f031d872f7d1440fd17833
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086636"
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