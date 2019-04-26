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
ms.openlocfilehash: a5acf1857309236727cd0bab4d9d981d814292b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786085"
---
# <a name="live-unit-testing-introduction"></a>Знакомство с Live Unit Testing

Live Unit Testing — это технология, которая была введена в Visual Studio 2017. Она выполняет модульные тесты автоматически в режиме реального времени по мере внесения изменений в код.

Динамическое модульное тестирование

- Позволяет более уверенно выполнять рефакторинг и изменять код. Live Unit Testing автоматически выполняет все соответствующие тесты в процессе редактирования кода для проверки того, не приведут ли изменения к ошибкам.

- Сообщает о том, достаточно ли полно модульные тесты охватывают код, и показывает код, который не охвачен модульными тестами. Live Unit Testing графически представляет объем протестированного кода в режиме реального времени. Это позволяет мгновенно узнать, сколько тестов охватывают каждую строку кода и какие строки не охватываются ни одним модульным тестом.

Если имеется решение, включающее в себя один или несколько проектов модульных тестов, вы можете включить Live Unit Testing, выбрав в меню Visual Studio верхнего уровня пункты **Тест** > **Live Unit Testing** > **Запуск**.

> [!NOTE]
> Функция Live Unit Testing доступна только в Visual Studio Enterprise Edition.

Дополнительные сведения о Live Unit Testing:

- См. подробнее о [начале работы с Live Unit Testing в Visual Studio](live-unit-testing-start.md).

- Прочитайте подробную документацию [Использование Live Unit Testing в Visual Studio Enterprise Edition](live-unit-testing.md).

- Ознакомьтесь с [вопросами и ответами о Live Unit Testing](live-unit-testing-faq.md), чтобы узнать о новых возможностях Live Unit Testing, а также получить советы и рекомендации по работе.

- Просмотрите видео на канале Channel 9 с обзором функции Live Unit Testing и ее возможностей. </p>

   > [!VIDEO https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105/player]

## <a name="related-resources"></a>Связанные ресурсы

- [Средства тестирования кода](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Модульное тестирование кода](unit-test-your-code.md)
