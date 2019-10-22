---
title: 'IDebugDocumentHost:: путь | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 33ebcde4cf1db28e199f13fae720374bd1b64763
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569279"
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
 заполняет Строка, содержащая длинное имя.  
  
 `pfIsOriginalFile`  
 заполняет Флаг, который имеет значение true, если `pbstrLongName` ссылается на исходный файл документа; в противном случае — значение false.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Невозможно создать или определить исходный файл.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает полный путь и имя исходного файла документа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)