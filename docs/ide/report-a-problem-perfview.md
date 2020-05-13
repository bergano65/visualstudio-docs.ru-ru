---
title: Сбор журналов трассировки событий с помощью PerfView
ms.date: 09/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 24d72e9630506ecc3d25fcc75e51eeb84f619e53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271164"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Сбор журналов трассировки событий с помощью PerfView

PerfView — это инструмент, позволяющий создавать файлы ETL (журналов трассировки событий) с помощью функции [трассировки событий для Windows](/windows/desktop/ETW/event-tracing-portal), которые могут оказаться полезными при устранении некоторых проблем, связанных с Visual Studio. Когда вы сообщаете о проблеме, иногда группа разработчиков может попросить вас запустить PerfView для сбора дополнительных сведений.

## <a name="install-perfview"></a>Установка PerfView

Скачайте PerfView из [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Запуск PerfView

1. Щелкните правой кнопкой мыши файл **PerfView.exe** в проводнике Windows и выберите **Запуск от имени администратора**.
1. В меню Collect (Сбор) выберите **Collect** (Выполнить сбор).
1. Установите флажки **Zip** (Создание архива), **Merge** (Слияние) и **ThreadTime** (Время потока).
1. Для параметра **Circular MB** (Количество МБ для циклического использования) увеличьте значение до 1000.
1. Измените значение параметра **Current Dir** (Текущий каталог), чтобы данные трассировки ETL сохранялись в указанную папку и файл данных, если планируется выполнять сбор несколько раз.
1. Чтобы начать запись данных, нажмите кнопку **Start Collection** (Начать сбор).
1. Чтобы остановить запись данных, нажмите кнопку **Stop Collection** (Остановить сбор). ZIP-файл PrefView.etl сохранится в указанном каталоге.

PerfView может хранить только последние данные, которые соответствуют хранящимся в буфере. Таким образом, попробуйте остановить сбор данных сразу же после того, как Visual Studio начнет зависать или медленно работать. Не выполняйте сбор дольше 30 секунд после обнаружения проблемы.

Дополнительные сведения см. в [руководствах по PerfView на канале Channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
