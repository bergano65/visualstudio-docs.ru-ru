---
title: SDK моделирования для Visual Studio — доменные языки
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df931cf5cb9034a868f412a344e26a58e6006455
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942782"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK моделирования для Visual Studio — доменные языки

Используя пакет SDK моделирования для Visual Studio, можно создать мощные модели с использованием средства разработки, которые можно интегрировать в Visual Studio. Таким же образом можно создать одно или несколько определений моделей и интегрировать их в набор средств.

Ключевой элемент MSDK — определение модели, которая создается для представления концепций в бизнес-сфере. Вы можете заключить модель с разнообразными средствами, например Схематическое представление, возможность создания кода и других артефактов, команды преобразования модели и могут взаимодействовать с кодом и другие объекты в Visual Studio. При разработке модели ее можно объединить с другими моделями и средствами для создания эффективного набора инструментов, предназначенных для разработки.

MSDK позволяет быстро разработать модель в виде доменного языка (DSL). Разработка начинается с использования специализированного редактора для определения схемы или абстрактного синтаксиса вместе с графической нотацией. На основе этого определения пакет VMSDK создает:

- реализацию модели со строго типизированным интерфейсом API, работающим в магазине на основе транзакций;

- обозреватель с иерархической структурой;

- графический редактор, в котором пользователи могут просматривать модель или ее части, которые вы определяете;

- методы сериализации, сохраняющие ваши модели в доступном для чтения формате XML;

- средства для создания программного кода и других артефактов, использующих шаблон текста.

Все эти средства можно настраивать и расширять. Расширения интегрируются таким образом, что сохраняются возможности обновления определения доменного языка и повторного создания функций без потери расширений.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Связанные записи в блогах](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

Руководство по передовым технологиям и устранению неполадок, см. в статье [форум по Visual Studio DSL и расширяемость средств моделирования](http://go.microsoft.com/fwlink/?LinkID=186074).

## <a name="in-this-section"></a>В этом разделе
 [Начало работы с доменными языками](../modeling/getting-started-with-domain-specific-languages.md)

 [Сведения о моделях, классах и отношениях](../modeling/understanding-models-classes-and-relationships.md)

 [Определение доменного языка](../modeling/how-to-define-a-domain-specific-language.md)

 [Настройка и расширение доменного языка](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Проверка в доменных языках](../modeling/validation-in-a-domain-specific-language.md)

 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Создание кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md)

 [Общие сведения о коде доменных языков](../modeling/understanding-the-dsl-code.md)

 [Настройка хранилища файлов и XML-сериализации](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Развертывание решений на доменных языках](../modeling/deploying-domain-specific-language-solutions.md)

 [Создание доменного языка на основе Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Создание доменного языка на основе WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Практическое руководство. Расширение конструктора доменного языка](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Выпуски Visual Studio, поддерживаемые пакетом SDK визуализации и моделирования](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Практическое руководство. Перенос доменного языка в новой версии](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Справка по API SDK моделирования для Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
