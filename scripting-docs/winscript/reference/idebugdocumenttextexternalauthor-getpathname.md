---
title: IDebugDocumentTextExternalAuthor::GetPathName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5739e7cb0cb12661ee5683051fb7b687e62dfde4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978758"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Возвращает полный путь к файлу и имя документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrLongName`  
 [out] Строка, содержащая полный путь и имя файла.  
  
 `pfIsOriginalFile`  
 [out] Логическое значение, указывающее, если путь и имя файла см. в исходный документ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Невозможно создать или определить исходный файл.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает полный путь к файлу и имя документа.  
  
 Если `pfIsOriginalFile` имеет значение FALSE, путь и имя файла в `pbstrLongName` ссылаться на только что созданный временный файл.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)