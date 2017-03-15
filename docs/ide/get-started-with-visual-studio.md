---
title: "Начало работы с Visual Studio | Документы Майкрософт"
description: "Основные сведения о том, как приступить к работе с Visual Studio"
ms.custom: 
ms.date: 12/05/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, getting started
ms.assetid: 38e90339-1da5-410c-8ba4-437fc556cba7
caps.latest.revision: 65
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 27493b53229d9ceb6bc215fcf3d57a60fe4358b0
ms.openlocfilehash: 452f8dbd2c7eb4bcc2f0310da1f04c6dd031f629
ms.lasthandoff: 02/22/2017

---
# <a name="get-started-with-visual-studio"></a>Начало работы с Visual Studio

Visual Studio является мощным инструментом для разработки приложений. Скачайте и установите [Visual Studio](https://aka.ms/vs/15/preview/vs_enterprise), если это еще не сделано. Дополнительные сведения о скачивании и настройке Visual Studio см. в видеоролике [Начало работы с Visual Studio: настройка интегрированной среды разработки](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1).

## <a name="visual-studio-tour"></a>Обзор Visual Studio
Visual Studio содержит группу окон инструментов, меню и панелей инструментов, которые в совокупности называются интегрированной средой разработки или IDE. Интегрированная среда разработки Visual Studio упрощает выполнение различных задач разработки. Ниже приведен краткий обзор элементов интегрированной среды разработки, которые будут использоваться чаще всего.

### <a name="code-editor"></a>Редактор кода
Одно из наиболее часто используемых окон инструментов в Visual Studio для написания, просмотра кода и навигации по нему.

![Редактор кода](../ide/media/VSIDE_CodeWindow.png)

По мере ввода кода редактор кода позволяет быстро и легко создавать и находить код, предоставляя такие функции, как завершение инструкций, цветовое выделение синтаксиса, режим сопоставления и многое другое. Дополнительные сведения см. в видеоролике [Начало работы с Visual Studio: редактирование кода и перемещение по нему](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5).

Некоторые типы решений могут содержать формы, например WPF или Windows Forms. В таких случаях открывается визуальный конструктор, позволяющий визуально добавлять в форму такие элементы управления, как кнопки и списки.

### <a name="solution-explorer"></a>обозреватель решений

Перечень всех файлов кода находится в окне **Обозреватель решений**. Обозреватель решений позволяет упорядочить код путем объединения файлов в решения и проекты. Проект, выделенный полужирным шрифтом, называется запускаемым проектом. Это первый код, который выполняется при запуске решения. Запускаемый проект можно сменить. Дополнительные сведения см. в видеоролике [Начало работы с Visual Studio: основные компоненты интегрированной среды разработки](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK).

![Обозреватель решений со свернутыми узлами](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 Помимо решений и проектов, в обозревателе решений содержится список всех файлов в каждом проекте, которые отображаются при развертывании узла проекта. Каждый проект содержит один или несколько файлов, таких как файлы исходного кода, и файлов ресурсов, таких как изображения или библиотеки.

![обозреватель решений](../ide/media/VSIDE_SolutionExplorer3.png)

Чтобы просмотреть свойства для решений, проектов и файлов, выберите пункт **Свойства** в контекстном меню (вызываемом щелчком правой кнопкой мыши) или в строке меню выберите **"Вид", "Свойства"**.

![Окно \"Свойства\"](../ide/media/VSIDE_SolutionExplorer4.png)

Чтобы приступить к созданию кода, не нужно создавать решение или проект. Можно просто перейти к файлам кода (например, клонированным из репозитория Git), открыть их в Visual Studio и сразу же начать их редактировать. Файлы появятся в обозревателе решений с цветовым выделением синтаксиса, заполнением базовых инструкций и т. д. так же, как традиционные решения. Дополнительные сведения см. в статье [Open Any Folder](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) (Открытие папки).

### <a name="toolbar-and-menus"></a>Панели инструментов и меню
Панели инструментов и команды меню предназначены для запуска проекта, создания решений, сохранения файлов и выполнения многих других задач. Например, подготовив код к отладке, можно нажать кнопку **Запуск** на панели инструментов или выбрать в строке меню **"Отладка", "Начать отладку"**. Чтобы создать новое решение, нажмите кнопку **Создать проект** или в строке меню выберите **"Файл", "Создать", "Проект"** и т. д.

![Панель инструментов Visual Studio](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

Обратите внимание, что значки панели инструментов и команды зависят от контекста, то есть выбранного элемента.

### <a name="team-explorer"></a>Командный обозреватель
**Team Explorer** позволяет подключаться к инструментам управления версиями, таким как [Git](https://git-scm.com/) и [система управления версиями Team Foundation (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview), для локального хранения кода или его использования вместе с другими пользователями в размещенной службе. Его также можно использовать для отслеживания задач и многого другого.

Дополнительные сведения см. в видеороликах [Начало работы с Visual Studio: основные компоненты интегрированной среды разработки](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) и [Начало работы с Visual Studio: открытие проекта из системы управления версиями](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3).

![Командный обозреватель](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>окно выходных данных
В окно **Вывод** Visual Studio отправляет уведомления, такие как сообщения об отладке и ошибках, предупреждения компилятора, сообщения о состоянии публикаций и многие другие. Каждый тип сообщения имеет собственную вкладку.

![окно выходных данных](../ide/media/VSIDE_OutputWindow.png)

Дополнительные сведения о том, как использовать окно вывода для отладки, см. в статье [Окно "Вывод" при отладке в Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/).

## <a name="first-steps"></a>Первые шаги
- **Установка** — дополнительные сведения о скачивании и установке Visual Studio см. в статье [Установка](https://go.microsoft.com/fwlink/?linkid=833223).
- **Основы** — дополнительные сведения о работе в Visual Studio см. в статье [Начало разработки в Visual Studio](../ide/get-started-developing-with-visual-studio.md).
- **Параметры** — настройте Visual Studio в соответствии с вашим стилем работы. См. статью [Персонализация интегрированной среды разработки Visual Studio](https://msdn.microsoft.com/en-us/library/mt269425.aspx).
- **Учебники** — для получения дополнительных сведений о разработке кода в Visual Studio изучите учебник, например [Начало работы с Visual C# и Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171.aspx) или [Начало работы с C++ в Visual Studio](https://msdn.microsoft.com/en-us/library/jj620919.aspx).
- **Видео** — чтобы узнать о других возможностях и аспектах Visual Studio, ознакомьтесь с видеоматериалами на [канале Microsoft Visual Studio](https://www.youtube.com/user/VisualStudio/videos) на YouTube или с видео по Visual Studio на канале [Channel 9](https://channel9.msdn.com/Tags/visual+studio).

## <a name="access-cloud-based-resources"></a>Доступ к облачным ресурсам

Если вы хотите использовать облачные ресурсы в приложении или игре, необходимо включить [службы Azure](https://azure.microsoft.com/en-us/services/). Чтобы получить пакет Azure SDK для .NET, установите рабочую нагрузку Azure рабочей нагрузки с помощью нового установщика Visual Studio. Установленные пакеты находятся на одном функциональном уровне с версией 2.9.5 пакета SDK. Для этой и всех будущих версий Visual Studio пакет Azure SDK для .NET будет доступен только из установщика Visual Studio.

После установки пакета Azure SDK для .NET в Visual Studio будет доступно новое окно инструмента **Cloud Explorer**. Cloud Explorer позволяет просматривать ресурсы Azure и управлять ими в Visual Studio. Если для выполнения конкретной операции требуется портал Azure, Cloud Explorer предоставит ссылки для перехода в нужное место на портале Azure.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

Дополнительные сведения об использовании Cloud Explorer см. в статье [Управление ресурсами Azure с помощью Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
Установив пакет SDK для Azure, вы получите [инструменты Visual Studio для Azure](https://www.visualstudio.com/vs/azure-tools/) и другие средства.

## <a name="tips-and-tricks"></a>Советы и рекомендации
Сведения о сочетаниях клавиш и полезные советы и рекомендации о максимально эффективном использовании Visual Studio см. в следующих материалах.
- [Getting Started with Visual Studio - Tips & Tricks](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4) (Начало работы с Visual Studio: советы и рекомендации)
- [Советы по повышению продуктивности при работе в Visual Studio](https://msdn.microsoft.com/en-us/library/jj153218.aspx)
- [Блог с советами и рекомендациями по Visual Studio](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)
- [C++ Debugging Tips and Tricks](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks) (Отладка C++: советы и рекомендации)
- [Getting Started with Visual Studio - Installing Visual Studio extensions](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7) (Начало работы с Visual Studio: установка расширений Visual Studio)

