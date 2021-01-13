---
title: BeginCapture | Документация Майкрософт
description: Используйте метод BeginCapture класса VsgDbg, чтобы начать интервал захвата, который будет завершен функцией EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 931e7ab05442a429c0b9e6468d42aadca942c1ee
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727969"
---
# <a name="begincapture"></a>BeginCapture
Начинает интервал захвата, который будет завершен функцией `EndCapture`.

## <a name="syntax"></a>Синтаксис

```C++
void BeginCapture();
```

## <a name="remarks"></a>Примечания
 Обычно интервал захвата охватывает подмножество из одного кадра, — как, например, когда требуется захватить данные графики только для определенного типа вызова рисования. Если интервал захвата распространяется до вызова метода Present, то захватываются два кадра графических данных. Первый кадр охватывает интервал между вызовом `BeginCapture` и вызовом метода Present; второй кадр охватывает интервал между первым событием Direct3D после вызова метода Present и вызовом `EndCapture`.

 Для захвата интервала необходимо подготовить приложение к захвату и записи данных графики, т. е. необходимо вызвать метод [Init](init.md) посредством экземпляра класса `VsgDbg`, прежде чем вызывать `BeginCapture` или `EndCapture`.

## <a name="see-also"></a>См. также
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)