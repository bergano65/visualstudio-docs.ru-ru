---
title: CaptureCurrentFrame | Документация Майкрософт
description: Используйте метод CaptureCurrentFrame класса VsgDbg для захвата оставшейся части текущего кадра в файл журнала графики.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d86ac7d23fa209560222415dce50f4e5ac508
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727948"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Захватывает оставшуюся часть текущего кадра в файл журнала графики.

## <a name="syntax"></a>Синтаксис

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Примечания
 Если в данный момент выполняется другой захват — например, запущенный функцией `BeginCapture` — тот захват завершается и записывается в журнал графики как отдельный кадр. Сразу же после этого диагностика графики начинает захват остатка текущего кадра, который также записывается как отдельный кадр. Окончание текущего кадра отмечено вызовом метода Present.

 Для захвата кадра необходимо подготовить приложение к захвату и записи данных графики, т. е. необходимо вызвать метод [Init](init.md) посредством экземпляра класса `VsgDbg`, прежде чем вызывать `CaptureCurrentFrame`.

## <a name="see-also"></a>См. также
- [Init](init.md)
- [BeginCapture](begincapture.md)