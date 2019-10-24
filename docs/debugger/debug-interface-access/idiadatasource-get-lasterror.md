---
title: 'Идиадатасаурце:: get_lastError | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48595dda70560f555533a1857f73db4d7bd20a86
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744977"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Возвращает имя файла для последней ошибки загрузки.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 претвал

заполняет Возвращает строку, содержащую имя PDB-файла, связанного с последней ошибкой загрузки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает последний код ошибки, вызванный операцией загрузки. Возвращает `E_INVALIDARG`, если параметр `pRetVal` имеет значение `NULL`.

## <a name="example"></a>Пример

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>См. также
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)