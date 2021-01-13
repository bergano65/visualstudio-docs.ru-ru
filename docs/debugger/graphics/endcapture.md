---
title: EndCapture | Документация Майкрософт
description: Используйте метод EndCapture класса VsgDbg для завершения интервала захвата, начатого функцией BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbdc8f2dc4fa3ad25be8674b9a46bf02179aa1d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727835"
---
# <a name="endcapture"></a>EndCapture
Завершает интервал захвата, начатый функцией `BeginCapture`.

## <a name="syntax"></a>Синтаксис

```C++
void EndCapture();
```

## <a name="remarks"></a>Примечания
 Обычно интервал захвата охватывает подмножество из одного кадра, — как, например, когда требуется захватить данные графики только для определенного типа вызова рисования. Если интервал захвата распространяется до вызова метода Present, то захватываются два кадра графических данных. Первый кадр охватывает интервал между вызовом `BeginCapture` и вызовом метода Present; второй кадр охватывает интервал между первым событием Direct3D после вызова метода Present и вызовом `EndCapture`.

 Для захвата интервала необходимо подготовить приложение к захвату и записи данных графики, т. е. необходимо вызвать метод [Init](init.md) посредством экземпляра класса `VsgDbg`, прежде чем вызывать `BeginCapture` или `EndCapture`.

## <a name="see-also"></a>См. также
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)