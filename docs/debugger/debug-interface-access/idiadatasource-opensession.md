---
title: 'Идиадатасаурце:: Опенсессион | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744922"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Открывает сеанс для запроса символов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Параметры
ппсессион

заполняет Возвращает объект [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , представляющий открытый сеанс.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.

|значения|Описание|
|-----------|-----------------|
|E_UNEXPECTED|Объект [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md) ранее не был инициализирован с источником символов.|
|E_INVALIDARG|Недопустимый параметр `ppSession`.|
|E_OUTOFMEMORY|Недостаточно памяти для открытия сеанса.|

## <a name="remarks"></a>Заметки
Этот метод открывает объект [IDiaSession](../../debugger/debug-interface-access/idiasession.md) для источника данных.

`IDiaSession` объекты реализуют запросы к источнику данных. Сеанс управляет одним адресным пространством для каждого набора отладочных символов. Если файл exe или DLL, описываемый символами источника данных, активен в нескольких диапазонах адресов (например, из-за загрузки нескольких процессов), следует использовать один сеанс для каждого диапазона адресов.

## <a name="example"></a>Пример

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>См. также
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
