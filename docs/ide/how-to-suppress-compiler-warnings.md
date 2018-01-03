---
title: "Практическое руководство. Отключение предупреждений компилятора | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d97695cae08352ea213ba02008ab99bef7f61c47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-compiler-warnings"></a>Практическое руководство. Отключение предупреждений компилятора
Журнал сборки можно упорядочить, указав один вид предупреждений компилятора или несколько, которые не должны входить в журнал. Например, этот метод можно использовать для просмотра некоторых (не всех) сведений, которые автоматически создаются при установке таких уровней детализации ведения журнала сборки, как "Обычный", "Подробный" или "Диагностический". Дополнительные сведения о детализации см. в статье [Практическое руководство. Просмотр, сохранение и настройка файлов журнала построения](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Отключение некоторых предупреждений для Visual C# и F# #
  
1.  В **обозревателе решений** выберите проект, в котором вы хотите отключить предупреждения.  
  
2.  В строке меню выберите **Вид**, **Страницы свойств**.  
  
3.  Перейдите на страницу **Сборка**.  
  
4.  В окне **Отключить предупреждения** укажите разделенные точкой с запятой коды ошибок предупреждений, которые необходимо отключить, а затем перестройте решение.  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>Отключение некоторых предупреждений для Visual C++  
  
1.  В **обозревателе решений** выберите проект или исходный файл, в котором хотите отключить предупреждения.  
  
2.  В строке меню выберите **Вид**, **Страницы свойств**.  
  
3.  Выберите категорию **Свойства конфигурации**, категорию **C/C++** и затем — страницу **Дополнительно**.  
  
4.  Выполните одно из следующих действий.  
  
    -   В окне **Отключить некоторые предупреждения** укажите разделенные точкой с запятой коды ошибок предупреждений, которые необходимо отключить.  
  
    -   В окне **Отключить некоторые предупреждения** щелкните **Изменить**, чтобы отобразить дополнительные параметры.  
  
5.  Нажмите кнопку **ОК**, а затем перестройте решение.  
  
## <a name="suppressing-warnings-for-visual-basic"></a>Отключение предупреждений для Visual Basic  
 Чтобы скрыть некоторые предупреждения компилятора для Visual Basic, измените VBPROJ-файл для проекта. Для отключения предупреждений по категориям можно также использовать [страницу компиляции, конструктор проектов](../ide/reference/compile-page-project-designer-visual-basic.md). Дополнительные сведения см. в статье [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Отключение некоторых предупреждений для Visual Basic  
  
1.  В **обозревателе решений** выберите проект, в котором вы хотите отключить предупреждения.  
  
2.  В строке меню выберите **Проект**, затем — **Выгрузить проект**.  
  
3.  В **обозревателе решений**откройте контекстное меню для своего проекта и выберите **Правка***имя_проекта***.vbproj**.  
  
     Файл проекта откроется в редакторе кода.  
  
4.  Найдите элемент `<NoWarn></NoWarn>` в конфигурации сборки, используемый для построения.  
  
     В следующем примере показан выделенный полужирным шрифтом элемент `<NoWarn></NoWarn>` для отладочной конфигурации сборки на платформе x86:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn></NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Добавьте один или несколько номеров предупреждений в качестве значения элемента `<NoWarn>`. Если вы указываете несколько номеров предупреждений, разделяйте их запятыми, как показано в следующем примере.  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  Сохраните изменения в VBPROJ-файле.  
  
7.  В строке меню выберите **Проект**, затем — **Перезагрузить проект**.  
  
8.  В строке меню последовательно выберите пункты **Сборка**, **Перестроить решение**.  
  
     В окне **Вывод** указанные предупреждения больше не отображаются.  
  
 Дополнительные сведения см. в статье [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Построение приложения](../ide/walkthrough-building-an-application.md)   
 [Практическое руководство. Просмотр, сохранение и настройка файлов журнала построения](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)
