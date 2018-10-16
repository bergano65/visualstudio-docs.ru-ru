---
title: Функцию автоматического приостановки в Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d75c02bf6b817d03492a15b1f827f94eaaf3e306
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31893931"
---
# <a name="automatic-feature-suspension"></a>Функцию автоматического приостановки

Если доступной системной памяти падает до 200 МБ или меньше, Visual Studio отображает следующее сообщение в редакторе кода:

![Текст предупреждения, приостановка полный анализ решения](../code-quality/media/fsa_alert.png)

Когда Visual Studio обнаруживает нехватки памяти, автоматически приостанавливает некоторых дополнительных функций, призванных помочь остается стабильной. Visual Studio продолжает работать как и прежде, но снижается производительность.

В условиях нехватки памяти выполняются следующие действия:

- Полный анализ решения для Visual C# и Visual Basic отключен.

- [Сборка мусора](/dotnet/standard/garbage-collection/index) выключен режим малой задержкой (GC) для Visual C# и Visual Basic.

- Visual Studio кэшей будут сброшены.

## <a name="improve-visual-studio-performance"></a>Повышения производительности Visual Studio

Советы и рекомендации по улучшению производительности Visual Studio при работе с большими решениями или условия нехватки памяти, в разделе [вопросы производительности для больших решений](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Полный анализ решения приостановлено

По умолчанию полный анализ решения включена для Visual Basic и отключена для Visual C#. Однако в условиях нехватки памяти, полный анализ решения автоматически отключается для Visual Basic и Visual C#, независимо от параметров в диалоговом окне параметров. Тем не менее, можно повторно включить полный анализ решения, выбрав **повторно включить** кнопку сведений панели появлением, выбрав **включить полный анализ решения** флажок в диалоговом окне Параметры или перезапустите Visual Studio. Диалоговое окно параметров всегда показывает текущее полное решение параметры анализа. Дополнительные сведения см. в разделе [как: Включение и отключение анализа всего решения](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>Сборка Мусора малой задержкой отключена

Чтобы снова включить режим сборки Мусора низкой задержкой, перезапустите Visual Studio. По умолчанию Visual Studio включает режим сборки Мусора небольшая задержка при вводе убедитесь, что текст не блокируют операции сборки Мусора. Тем не менее если нехватки памяти приводит к Visual Studio для отображения предупреждения автоматического приостановки, режим сборки Мусора низкой задержкой отключен для данного сеанса. Перезапустите Visual Studio повторно включает поведение по умолчанию глобального Каталога. Дополнительные сведения см. в разделе <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio кэшей, в записаны на диск

Если продолжить текущий сеанс разработки или перезапустите Visual Studio, немедленно очищаются все кэши Visual Studio, но начинается для повторного заполнения. Кэши сброшены включают кэши для следующих компонентов:

- Поиск всех ссылок

- Функция "Перейти к"

- Добавление директивы Using

Кроме того кэш, используемый для внутренних операций Visual Studio, также будут удалены.

> [!NOTE]
> Функцию автоматического приостановки предупреждение только один раз на основе каждого решения не на основе сеансов. Это означает, что, если переход от Visual Basic, Visual C# (или наоборот) и запуска в другое состояние нехватки памяти, можно возможно получить еще одно предупреждение приостановки функции автоматического.

## <a name="see-also"></a>См. также

- [Как: Включение и отключение полный анализ решения](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Основы сборки мусора](/dotnet/standard/garbage-collection/fundamentals)
- [Вопросы производительности для больших решений](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)