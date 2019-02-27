---
title: IDiaStackWalker | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ad74f92765ee449eab1e3089511a063e70d96a0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617071"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Предоставляет методы, чтобы сделать стек стека, используя сведения в PDB-файл.

## <a name="syntax"></a>Синтаксис

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
В следующей таблице показаны методы `IDiaStackWalker`.

|Метод|Описание|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Извлекает перечислитель кадр стека для x86 платформ.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Извлекает перечислитель кадр стека для типа конкретную платформу.|

## <a name="remarks"></a>Примечания
Этот интерфейс используется для получения списка кадров стека для загруженного модуля. Каждый из методов передается [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) object (реализовано клиентским приложением), который предоставляет сведения, необходимые для создания списка кадров стека.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Этот интерфейс получается путем вызова `CoCreateInstance` метод с идентификатором класса `CLSID_DiaStackWalker` и идентификатор интерфейса `IID_IDiaStackWalker`. В примере показано, как этот интерфейс получается.

## <a name="example"></a>Пример
В этом примере показано, как получить `IDiaStackWalker` интерфейс.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Требования
Заголовок: Dia2.h

Библиотека: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
