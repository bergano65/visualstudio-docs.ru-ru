---
title: "IDebugDocumentTextExternalAuthor::GetPathName | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextExternalAuthor.GetPathName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e5c27422d6b348d8c961d1555bfce07183e9e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Возвращает полный путь и имя документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrLongName`  
 [out] Строка, содержащая полный путь и имя файла.  
  
 `pfIsOriginalFile`  
 [out] Логическое значение, указывающее, если путь и имя файла см. в исходном документе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Не удается создать или определить исходный файл.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает полный путь и имя документа.  
  
 Если `pfIsOriginalFile` имеет значение FALSE, путь и имя файла в `pbstrLongName` ссылается на вновь созданный временный файл.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)