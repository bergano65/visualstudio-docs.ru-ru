---
title: IDiaDataSource::get_lastError | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8939a3eea7f89b71c7d901b600857d62da65abbc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956885"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Получает имя файла для последней ошибки загрузки.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out] Возвращает строку, содержащую имя файла PDB-файл, связанный с последней ошибки загрузки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает код последней ошибки, из-за операции загрузки. Возвращает `E_INVALIDARG` Если `pRetVal` параметр `NULL`.  
  
## <a name="example"></a>Пример  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)