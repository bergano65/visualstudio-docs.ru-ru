---
title: С помощью средства проверки C++ Core Guidelines | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1153f7a32c26946fafb1230699c4afcae976cd9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799565"
---
# <a name="using-the-c-core-guidelines-checkers"></a>С помощью средства проверки C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core Guidelines представляют собой переносимый набор рекомендации, правила и рекомендации о написании кода на C++, созданные экспертами C++ и конструкторы.  Visual Studio теперь поддерживает пакеты надстроек, которые создают дополнительные правила для кода, средства анализа, чтобы проверить код на соответствие C++ Core Guidelines и предложить улучшения.  
  
## <a name="the-c-core-guidelines-project"></a>Проект C++ Core Guidelines  
 Создан (Bjarne Stroustrup) и другими C++ Core Guidelines — это руководство по использованию современный C++, безопасно и эффективно. Рекомендации подчеркнуть статический строгая типизация и безопасность ресурсов. Они определять способы устранить или свести к минимуму наиболее подверженных ошибкам части языка и предлагают способы сделать код более простой и более высокую производительность надежным способом. Эти рекомендации обслуживаются Standard C++ Foundation. Дополнительные сведения см. в документации [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)и получить доступ к документации файлов проекта C++ Core Guidelines на [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft поддерживает усилия C++ Core Guidelines путем предоставления C++ Core Check правил анализа кода задает, что можно добавить в проекты с помощью пакета Nuget. Пакет называется Microsoft.CppCoreCheck, и оно доступно в [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Этот пакет требует, что у вас есть по крайней мере установлена среда Visual Studio 2015 с обновлением 1.  
  
 Пакет также устанавливает другой пакет как зависимость только заголовки рекомендация поддержки библиотеки (GSL). GSL также доступна на сайте GitHub в [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Включить правила C++ Core Check в анализе кода  
 Чтобы включить средства анализа кода C++ Core Check, установите пакет Microsoft.CppCoreCheck NuGet в каждый проект C++, который вы хотите проверить в среде Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Добавление пакета Microsoft.CppCoreCheck в проект  
  
1. В **обозревателе решений**, щелкните правой кнопкой мыши, чтобы открыть контекстное меню проекта в решении, которое вы хотите добавить пакет. Выберите **управление пакетами NuGet** открыть **диспетчер пакетов NuGet**.  
  
2. В **диспетчер пакетов NuGet** окно, и выполните поиск Microsoft.CppCoreCheck.  
  
    ![Окно диспетчера пакетов NuGet показан пакет CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Выберите пакет Microsoft.CppCoreCheck, а затем выберите **установить** кнопку, чтобы добавить правила в проект.  
  
   Пакет NuGet добавляет дополнительный файл целевых объектов MSBuild в проект, который вызывается при включении анализа кода в проекте. Этот файл .targets добавляет правила C++ Core Check как расширение дополнительные средства анализа кода в Visual Studio.  
  
   Вы можете включить анализ кода в проекте, выбрав **включить анализ кода в построении** флажок в **анализа кода** раздел **страницы свойств** диалоговое окно для ваш проект.  
  
   ![Страница свойств для параметров общие анализа кода](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Правила C++ Core Check становятся частью наборы правил по умолчанию при включении анализа кода. Поскольку эти правила C++ Core Check в стадии разработки, некоторые правила могут быть не готовы для использования на весь код, но может быть информативной во время разработки. Эти правила выпускаются в экспериментальном. Можно выбрать, следует ли выполнять правила отмененной или экспериментальный в свойствах проекта.  
  
   ![Страница свойств для параметров расширения анализа кода](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Чтобы включить или отключить наборов правил C++ Core Check, откройте **страницы свойств** диалоговое окно для вашего проекта. В разделе **свойства конфигурации**, разверните **анализа кода**, **расширения**. В раскрывающемся списке элемента управления рядом с полем **включить C++ Core Check (запущен)** или **включить C++ Core Check (экспериментальная функция)**, выберите **Да** или **нет**. Выберите **ОК** или **применить** для сохранения изменений.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Проверьте типы, границ и время существования  
 Пакет C++ Core Check в настоящее время содержит средства проверки для [безопасность типа](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [границ безопасности](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), и [безопасности времени существования](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) профилей.  
  
 Вот пример такого рода проблем, которые можно найти правила C++ Core Check:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 В этом примере показаны некоторые из предупреждений, которые можно найти правила C++ Core Check:  
  
- C26494 — правило Type.5: всегда Инициализируйте объект.  
  
- C26485 — правило Bounds.3: нет decay массива в указатель.  
  
- C26481 — правило Bounds.1: не используйте арифметику указателей. Взамен рекомендуется использовать `span`.  
  
  Если установлены и включены при компиляции кода C++ Core Check наборы правил анализа кода, первые два предупреждения выводятся, но третий подавляется. Ниже приведен результат сборки из образца кода.  
  
  **1 >---сборка начата: проект: CoreCheckExample, конфигурация: Debug Win32--**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj C:\Users\username\documents\visual studio 2015\P, "->"**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj C:\Users\username\documents\visual studio 2015\P, "->"**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (полный PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): предупреждение C26494: переменная «arr» является uninitializ**  
**конференции всегда Инициализируйте объект. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**ИДЕНТИФИКАТОР = 620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): предупреждение C26485: выражение «arr»: ни один массив для**  
 **decay указатель. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**==== Сборки: 1 — успешно, 0, с ошибками, 0 пропущено ====** The C++ Core Guidelines должны помогать вам в написании кода лучше и безопаснее. Тем не менее если у вас есть экземпляр, где не должно применяться правило или профиля, можно легко отключить его непосредственно в коде. Можно использовать `gsl::suppress` атрибут для предотвращения C++ Core Check обнаружения и создания отчетов любое нарушение правила в нем следующий блок кода. Можно пометить отдельные инструкции, чтобы отключить определенные правила. Можно даже отключить весь профиль границы, написав `[[gsl::suppress(bounds)]]` без включения номер конкретного правила.  
  
## <a name="use-the-guideline-support-library"></a>Использование библиотеки поддержки рекомендации  
 Пакет Microsoft.CppCoreCheck NuGet также устанавливается пакет, содержащий реализованный корпорацией Майкрософт библиотеки поддержки рекомендации (GSL). GSL также доступна в виде автономного в [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Эта библиотека является полезным, если вы хотите изучить основных рекомендаций. GSL содержит определения, которые позволяют заменять ошибкам конструкции с более безопасные альтернативы. Например, можно заменить `T*, length` пары параметров с `span<T>` типа. GSL является открытым исходным кодом, поэтому если вы хотите, взгляните на источников библиотеки, комментарий или участия в разработке документов проекта можно найти в [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).



