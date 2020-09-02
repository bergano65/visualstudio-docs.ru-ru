---
title: Предупреждения глобализации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7db942f410b9a6a8c2f12a044d0e48ad1ad19950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667585"
---
# <a name="globalization-warnings"></a>Предупреждения глобализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предупреждения глобализации поддерживают библиотеки и приложения, готовые к международному использованию.

## <a name="in-this-section"></a>в этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1300. Укажите MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md)|Чтобы окно сообщения для языков, в которых используется порядок чтения справа налево, отображалось правильно, методу Show следует передать члены RightAlign и RtlReading перечисления MessageBoxOptions.|
|[CA1301. Избегайте повторяющихся акселераторов](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Клавиша доступа, также называемая клавишей быстрого доступа, обеспечивает клавиатурный доступ к элементу управления с помощью клавиши ALT. Если несколько элементов управления имеют дублирующиеся клавиши доступа, поведение клавиши доступа определено нечетко.|
|[CA1302. Не указывайте прямо в коде строки, зависящие от языковых стандартов](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Перечисление System.Environment.SpecialFolder содержит члены, ссылающиеся на специальные системные папки. Расположение этих папок может различаться в разных ОС, пользователь может менять расположение этих папок, их имена могут быть локализованы. Метод Environment.GetFolderPath возвращает связанные с перечислением Environment.SpecialFolder расположения в локализованной форме, подходящей для использования на работающем в данный момент компьютере.|
|[CA1303. Не передавайте литералы в качестве локализованных параметров](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Внешне видимый метод передает строковый литерал в виде параметра конструктору или методу в библиотеке классов [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], и эта строка должна быть локализуемой.|
|[CA1304. Указывайте CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)|Метод или конструктор вызывает член, имеющий перегрузку, которая принимает параметр System.Globalization.CultureInfo, вместо того чтобы вызвать перегрузку, принимающую параметр CultureInfo. Если объект CultureInfo или System.IFormatProvider не предоставляется, значение по умолчанию, поставляемое перегруженным членом, может не оказать ожидаемого воздействия во всех языковых стандартах.|
|[CA1305. Указывайте IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)|Метод или конструктор вызывает один или несколько членов, имеющих перегрузки, которые принимают параметр System.IFormatProvider, вместо того чтобы вызвать перегрузку, принимающую параметр IFormatProvider. Если объект System.Globalization.CultureInfo или IFormatProvider не предоставляется, значение по умолчанию, поставляемое перегруженным членом, может не оказать ожидаемого воздействия во всех языковых стандартах.|
|[CA1306. Задавайте языковой стандарт для типов данных](../code-quality/ca1306-set-locale-for-data-types.md)|Язык и региональные параметры определяют представление элементов данных, таких как формат чисел, обозначение денежных единиц и порядок сортировки. При создании объектов DataTable или DataSet следует явным образом указывать языковой стандарт.|
|[CA1307. Указывайте StringComparison](../code-quality/ca1307-specify-stringcomparison.md)|В операции сравнения строк используется перегрузка метода, которая не задает параметр StringComparison.|
|[CA1308. Нормализуйте строки в верхний регистр](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Строки следует нормализовать в верхний регистр. Существует небольшая группа символов, которые после преобразования в нижний регистр не могут участвовать в круговом перемещении.|
|[CA1309. Используйте порядковый параметр StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Операция сравнения строк, не являющаяся лингвистической, не задает для параметра StringComparison ни значения Ordinal, ни значения OrdinalIgnoreCase. После явного задания для параметра значения StringComparison.Ordinal или StringComparison.OrdinalIgnoreCase код часто становится более надежным и правильным, кроме того, увеличивается скорость его выполнения.|
|[CA2101: укажите маршалирование для строковых аргументов P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Член неуправляемого кода допускает частично доверенные вызывающие объекты, имеет строковый параметр и не маршалирует строку явным образом. Это может стать причиной потенциальной уязвимости безопасности.|
