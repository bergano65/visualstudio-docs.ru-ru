---
title: Просмотр типов и отношений (конструктор классов)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- class diagrams
- types [Visual Studio], visualizing
- relationships, class diagrams
- types [Visual Studio], class diagrams
- relationships, visualizing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca553f4d7b0cf2704950967e5666981ee84eda67
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="view-types-and-relationships-class-designer"></a>Просмотр типов и отношений (конструктор классов)

**Конструктор классов** использует диаграммы классов для отображения сведений о типах, например о составляющих их элементах и отношениях между ними. Визуализация этих сущностей фактически является динамическим представлением кода. Это означает, что можно изменять типы в конструкторе, а затем просматривать эти правки в исходном коде сущности. Аналогичным образом, диаграмма классов синхронизируется с изменениями, вносимыми для сущностей в коде.

> [!NOTE]
> Если проект содержит диаграмму классов и еще один проект ссылается на тип, который находится в другом проекте, диаграмма классов не отображает этот тип до сборки проекта для него. Аналогичным образом, диаграмма не отображает изменения кода внешней сущности, пока вы не перестроите проект с этой сущностью.

## <a name="see-also"></a>См. также

- [Разработка и просмотр классов и типов](designing-and-viewing-classes-and-types.md)
- [Рефакторинг классов и типов](refactoring-classes-and-types.md)
- [Практическое руководство. Настройка схем классов](how-to-customize-class-diagrams.md)
- [Работа с диаграммами классов](working-with-class-diagrams.md)