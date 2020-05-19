---
title: BeginCapture | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736145"
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