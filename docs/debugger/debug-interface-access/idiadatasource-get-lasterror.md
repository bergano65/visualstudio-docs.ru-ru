---
title: IDiaDataSource::get_lastError | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: e197262b84fcf964afb74f85e86ff384daa26c9e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819841"
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
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)