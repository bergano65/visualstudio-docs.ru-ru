---
title: IDiaStackWalker::getEnumFrames2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35886ea0456426c30c44d5fd8e90399d4a2143ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837944"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Извлекает перечислитель кадр стека для типа конкретную платформу.

## <a name="syntax"></a>Синтаксис

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Параметры
 `cpuid`

[in] Значение из [перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) перечисления, указывающее тип платформы.

 `pHelper`

[in] Вспомогательный метод [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) объекта.

 `ppEnum`

[out] Возвращает [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) объект, содержащий список [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) объектов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Для получения списка кадр стека для только что x86 платформы, вызов [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) метод.

## <a name="see-also"></a>См. также
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [Перечисление CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)