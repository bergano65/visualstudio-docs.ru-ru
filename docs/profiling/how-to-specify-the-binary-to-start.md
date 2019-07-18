---
title: Как выполнить Указание двоичного файла для запуска | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a03bf203e5078bdbdf6327ec7bda186613a25c03
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996132"
---
# <a name="how-to-specify-the-binary-to-start"></a>Как выполнить Определение двоичного файла для запуска

Для профилирования двоичных файлов, таких как библиотеки DLL, необходимо ввести сведения в диалоговом окне **Страницы свойств \<целевой объект>**. Эти сведения указывают расположение проекта DLL для вызывающего приложения.

1. В **обозревателе производительности** щелкните правой кнопкой мыши целевой двоичный файл и выберите пункт **Свойства**.

2. В диалоговом окне **Страницы свойств** щелкните **Запуск**.

3. Установите флажок **Переопределить свойства проекта**.

4. В текстовом поле **Исполняемый файл для запуска** укажите расположение файла.

5. В текстовом поле **Аргументы** укажите аргументы, необходимые для запуска приложения.

6. В текстовом поле **Рабочий каталог** укажите расположение каталога.

7. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)