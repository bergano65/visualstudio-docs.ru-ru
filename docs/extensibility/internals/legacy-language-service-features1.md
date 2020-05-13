---
title: Особенности Устаревшей Языковой Службы1 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707400"
---
# <a name="legacy-language-service-features"></a>Функции языковой службы прежних версий
Языковая служба управляемой структуры пакетов (MPF) может поддерживать одну или несколько [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] функций, таких как выделение синтаксиса, IntelliSense и проверка точки разрыва. Каждая функция может быть реализована независимо от других, но все они требуют парсера и сканера, за исключением синтаксиса подсветки, которая требует только сканера.

## <a name="in-this-section"></a>В этом разделе
- [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки соответствия языковой пары, также известной как соответствие скобки.

- [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки комментариев и некомментируть выбранный код.

- [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Описывает, что требуется для поддержки свойств документов, встроенных в исходный файл.

- [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки изложения путем реализации скрытых регионов.

- [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки кодов переформатирования.

- [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки фрагментов кода, которые являются сегментами кода, которые вставляются и могут быть отредактированы.

- [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Описывает то, что требуется для поддержки операции IntelliSense Parameter Info для отображения подписи метода при найме метода.

- [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки операции IntelliSense Быстрая информация для отображения информации об идентификаторе.

- [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки операции завершения выполнения участников IntelliSense для выбора участника пространства имен из списка.

- [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки операции IntelliSense Complete Word для завершения частично набранных слов.

- [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Описывает, что языковая служба может сделать для поддержки окна **Autos** во время отладки.

- [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Описывает, как использовать **панель «Навигация»** в верхней части представления редактора для обеспечения быстрой навигации любому типу или члену файла, отображаемому в этом представлении.

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Описывает то, что требуется для поддержки выделения синтаксиса исходного кода.

- [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Описывает, что языковая служба может сделать для поддержки проверки моментов проверки за пределами отладчика.

## <a name="related-sections"></a>Связанные разделы
- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Описывает парсер и сканер, необходимые для реализации всех функций языковой службы, используюейейейкоторой платформу управляемого пакета.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Описывает, что необходимо для реализации языковой службы с помощью MPF.

- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Описывает шаги, которые необходимы для регистрации языковой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]службы на основе MPF с помощью.

- [Использование технологии IntelliSense](../../ide/using-intellisense.md)

 Объясняет, как IntelliSense упрощает доступ к ссылкам на язык.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Предоставляет информацию о том, как использовать платформу управляемого пакета (MPF) для реализации полнофункциональных языковых услуг в управляемом коде.
