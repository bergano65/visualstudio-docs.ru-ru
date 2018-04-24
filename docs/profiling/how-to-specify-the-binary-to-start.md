---
title: Практическое руководство. Указание двоичного файла для запуска | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac87c771cf6d9515f3eae8d82f7d0d40fa6590a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-specify-the-binary-to-start"></a>Практическое руководство. Указание двоичного файла для запуска

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