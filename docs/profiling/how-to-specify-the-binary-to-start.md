---
title: Указание двоичного файла для запуска | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8b3aec9448c6493350683dc9f0bec0cc2d60fa82
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851337"
---
# <a name="how-to-specify-the-binary-to-start"></a>Практическое руководство. Определение двоичного файла для запуска

Для профилирования двоичных файлов, таких как библиотеки DLL, необходимо ввести сведения в диалоговом окне **\<Target>Страницы свойств**. Эти сведения указывают расположение проекта DLL для вызывающего приложения.

1. В **обозревателе производительности** щелкните правой кнопкой мыши целевой двоичный файл и выберите пункт **Свойства**.

2. В диалоговом окне **Страницы свойств** щелкните **Запуск**.

3. Установите флажок **Переопределить свойства проекта**.

4. В текстовом поле **Исполняемый файл для запуска** укажите расположение файла.

5. В текстовом поле **Аргументы** укажите аргументы, необходимые для запуска приложения.

6. В текстовом поле **Рабочий каталог** укажите расположение каталога.

7. Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
