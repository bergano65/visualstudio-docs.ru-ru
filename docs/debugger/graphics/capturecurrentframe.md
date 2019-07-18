---
title: CaptureCurrentFrame | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec67013b41a5ec8876866044355534c42bfe2ee0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848710"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Захватывает оставшуюся часть текущего кадра в файл журнала графики.

## <a name="syntax"></a>Синтаксис

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Примечания
 Если в данный момент выполняется другой захват — например, запущенный функцией `BeginCapture` — тот захват завершается и записывается в журнал графики как отдельный кадр. Сразу же после этого диагностика графики начинает захват остатка текущего кадра, который также записывается как отдельный кадр. Окончание текущего кадра отмечено вызовом метода Present.

 Для захвата кадра необходимо подготовить приложение к захвату и записи данных графики — то есть вам необходимо вызвать метод [Init](init.md) через экземпляр `VsgDbg` класса перед вызовом метода `CaptureCurrentFrame`.

## <a name="see-also"></a>См. также
- [Init](init.md)
- [BeginCapture](begincapture.md)