---
title: EndCapture | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ae024f0d91c980fa8e787b21c93d32a6431203e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695535"
---
# <a name="endcapture"></a>EndCapture
Завершает интервал захвата, начатый функцией `BeginCapture`.

## <a name="syntax"></a>Синтаксис

```C++
void EndCapture();
```

## <a name="remarks"></a>Примечания
 Обычно интервал захвата охватывает подмножество из одного кадра, — как, например, когда требуется захватить данные графики только для определенного типа вызова рисования. Если интервал захвата распространяется до вызова метода Present, то захватываются два кадра графических данных. Первый кадр охватывает интервал между вызовом `BeginCapture` и вызовом метода Present; второй кадр охватывает интервал между первым событием Direct3D после вызова метода Present и вызовом `EndCapture`.

 Для захвата интервала необходимо подготовить приложение к захвату и записи данных графики — то есть вам необходимо вызвать метод [Init](init.md) через экземпляр `VsgDbg` класса перед вызовом метода `BeginCapture` или `EndCapture`.

## <a name="see-also"></a>См. также раздел
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)