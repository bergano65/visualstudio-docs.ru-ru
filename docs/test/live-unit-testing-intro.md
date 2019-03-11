---
title: Знакомство с Live Unit Testing
description: Сведения о преимуществах функции Live Unit Testing и ее использовании при модульном тестировании проектов.
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 7cdf118ef901e607d24609e521325e27b90d345b
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222018"
---
# <a name="introducing-live-unit-testing"></a>Знакомство с Live Unit Testing

Live Unit Testing — это технология, которая была введена в Visual Studio 2017. Она выполняет модульные тесты автоматически в режиме реального времени по мере внесения изменений в код. Динамическое модульное тестирование

- Позволяет более уверенно выполнять рефакторинг и изменять код. Live Unit Testing автоматически выполняет все соответствующие тесты в процессе редактирования кода для проверки того, не приведут ли изменения к ошибкам.

- Сообщает о том, достаточно ли полно модульные тесты охватывают код, и показывает код, который не охвачен модульными тестами. Live Unit Testing графически представляет объем протестированного кода в режиме реального времени. Это позволяет мгновенно узнать, сколько тестов охватывают каждую строку кода и какие строки не охватываются ни одним модульным тестом.

Если имеется решение, включающее в себя один или несколько проектов модульных тестов, вы можете включить Live Unit Testing, выбрав в меню Visual Studio верхнего уровня пункты **Тест** > **Live Unit Testing** > **Запуск**.

Дополнительные сведения о Live Unit Testing:

- Ознакомьтесь с вводным учебником [Начало работы с Live Unit Testing в Visual Studio](live-unit-testing-start.md).

- Прочитайте подробную документацию [Использование Live Unit Testing в Visual Studio Enterprise Edition](live-unit-testing.md).

- Ознакомьтесь с [вопросами и ответами о Live Unit Testing](live-unit-testing-faq.md), чтобы получить сведения о новых возможностях в Live Unit Testing, а также советы и приемы по использованию Live Unit Testing.

- Просмотрите видео на канале Channel 9 с обзором функции Live Unit Testing и ее возможностей. </p>

   > [!VIDEO https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105/player]

## <a name="related-resources"></a>Связанные ресурсы

- [Средства тестирования кода](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Модульное тестирование кода](unit-test-your-code.md)
