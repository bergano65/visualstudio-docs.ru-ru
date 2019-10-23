---
title: 'IDiaSession:: Финдфилебид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aafdd2270606ba6e56713e9166dbae2b8c635b41
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742273"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Извлекает исходный файл по идентификатору исходного файла.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `uniqueId`

окне Указывает идентификатор исходного файла.

 `ppResult`

заполняет Возвращает объект [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , представляющий извлеченный исходный файл.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Идентификатор исходного файла — это уникальное значение, используемое внутренним образом для пакета SDK DIA, чтобы сделать все исходные файлы уникальными. Этот метод обычно используется внутри пакета SDK DIA.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)