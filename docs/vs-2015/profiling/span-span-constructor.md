---
title: Конструктор span::span | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df6df731de90a9aad9e6cc637b3f218e481b66b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198299"
---
# <a name="spanspan-constructor"></a>Конструктор span::span

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Инициализирует новый экземпляр класса `span`.

## <a name="syntax"></a>Синтаксис

```
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Параметры

`_Series` Допустимый контекст набора маркеров.

`_Format` Строка составного формата, содержащая текст, перемежаемый нулями или другими элементами форматирования, которые соответствуют объектам в списке аргументов.

`_Importance` Уровень важности.

`_Category` Категория.

## <a name="requirements"></a>Требования

**Заголовок:** cvmarkersobj.h

**Пространство имен:** Concurrency::diagnostic

## <a name="see-also"></a>См. также:

[Класс span](../profiling/span-class.md)
