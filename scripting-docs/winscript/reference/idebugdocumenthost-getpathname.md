---
title: IDebugDocumentHost::GetPathName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c33844ade2367ffeb7690306a5febbabde2f016
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096035"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Возвращает полный путь и имя исходного файла документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrLongName`  
 [out] Строка, содержащая длинное имя.  
  
 `pfIsOriginalFile`  
 [out] Флаг то есть значение true, если `pbstrLongName` ссылается на исходный файл для документа, значение false в противном случае.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Файл источника не может быть создано или определить.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает полный путь и имя исходного файла документа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)