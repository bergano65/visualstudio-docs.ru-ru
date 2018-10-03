---
title: 'Пошаговое руководство: Отладка веб-формы | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aff54238649947f578535dee2b813aa4daa90681
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559280"
---
# <a name="walkthrough-debugging-a-web-form"></a>Пошаговое руководство. Отладка веб-формы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: отладка веб-формы](https://docs.microsoft.com/visualstudio/debugger/walkthrough-debugging-a-web-form).  
  
Шаги данного руководства иллюстрируют способ отладки веб-приложений [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], также известных как веб-формы. Оно показано, как для запуска и остановки выполнения, задавать точки останова и просматривать переменные в **Watch** окна.  
  
> [!NOTE]
>  Для выполнения данного руководства необходимо обладать правами администратора на сервере. По умолчанию процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], aspnet_wp.exe или w3wp.exe, выполняется как процесс [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Для отладки [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] необходимо обладать правами администратора на компьютере, на котором выполняется [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Дополнительные сведения см. в разделе [требования к системе](../debugger/aspnet-debugging-system-requirements.md).  
  
 Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от действующих параметров или выпуска среды. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Создание веб-формы  
  
1.  Если какое-либо решение уже открыто, закройте его.  
  
2.  На **файл** меню, щелкните **New**, а затем нажмите кнопку **веб-сайт**.  
  
     **Новый веб-сайт** откроется диалоговое окно.  
  
3.  В **шаблоны** панели щелкните **веб-сайт ASP.NET**.  
  
4.  На **расположение** строка, нажмите кнопку **HTTP** из списка и в текстовом поле введите **http://localhost/WebSite**.  
  
5.  В **языка** выберите **Visual C#** или **Visual Basic**.  
  
6.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] создаст новый проект и отобразит исходный код HTML, создаваемый по умолчанию. Он также создает новый виртуальный каталог с именем **веб-сайт** под **Default Web Site** в службах IIS.  
  
7.  Нажмите кнопку **разработки** вкладке на нижней границе окна.  
  
8.  Нажмите кнопку **элементов** вкладку на левом поле, или выберите ее в **представление** меню.  
  
     Откроется **Панель элементов** .  
  
9. В **элементов**, нажмите кнопку **кнопку** управления и добавить его в рабочую область конструирования Default.aspx.  
  
10. В **элементов**, нажмите кнопку **Textbox** и перетащите элемент управления в область конструирования Default.aspx.  
  
11. Дважды щелкните сброшенный в конструктор элемент управления Button.  
  
     Откроется страница кода: Default.aspx.cs для языка C# или Default.aspx.vb для языка [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Курсор должен находиться в тексте функции `Button1_Click`.  
  
12. В функции `Button1_Click` добавьте следующий код:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. В меню **Сборка** выберите **Собрать решение**.  
  
     Проект должен быть построен без ошибок.  
  
     Теперь все готово для того, чтобы начать отладку.  
  
### <a name="to-debug-the-web-form"></a>Отладка веб-формы  
  
1.  В окне Default.aspx.cs или Default.aspx.vb щелкните левую границу рядом с добавленной текстовой строкой:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Появится красная точка, и текст строки будет выделен красным цветом. Красная точка представляет точку останова. Если приложение запускается из отладчика, выполнение этого приложения будет приостановлено отладчиком на строке с помеченным кодом. После этого можно просмотреть состояние приложения и произвести его отладку. Дополнительные сведения см. в разделе [точки останова](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  В меню **Отладка** щелкните **Начать отладку**.  
  
3.  **Отладка не включена** откроется диалоговое окно. Выберите **изменить файл Web.config для включения отладки** и нажмите кнопку **ОК**.  
  
     Будет запущен обозреватель Internet Explorer, в котором будет отображена только что созданная страница.  
  
4.  Нажмите кнопку в Internet Explorer.  
  
     В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] будет отображена строка кода в странице кода Default.aspx.cs или Default.aspx.vb, на которой была поставлена точка останова. Эта строка будет выделена желтым цветом. Теперь можно просматривать переменные в приложении и управлять его выполнением. После завершения выполнения приложение ожидает команды пользователя.  
  
5.  На **Отладка** меню, щелкните **Windows**, нажмите кнопку **Контрольные значения**, а затем нажмите кнопку **Контрольные значения 1**.  
  
6.  В **Watch** введите **TextBox1.Text**.  
  
     **Watch** окне отображается значение переменной `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  На **Отладка** меню, щелкните **шаг с обходом**.  
  
     Значение `TextBox1.Text` изменения в **Watch** окно для чтения:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  На **Отладка** меню, щелкните **Продолжить**.  
  
9. Снова нажмите кнопку в Internet Explorer.  
  
     Выполнение снова будет приостановлено по достижении точки останова.  
  
10. В окне Default.aspx.cs или Default.aspx.vb щелкните красную точку на левой границе.  
  
     Точка останова будет удалена.  
  
11. На **Отладка** меню, щелкните **остановить отладку**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Присоединение отладчика к веб-форме  
  
1.  В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] можно присоединить отладчик к выполняющемуся процессу. Для повышения эффективности отладки скомпилируйте исполняемый файл как отладочную версию с файлами символов (PDB).  
  
2.  В окне Default.aspx.cs или Default.aspx.vb щелкните левую границу, чтобы снова создать точку останова на добавленной строке:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  На **Отладка** меню, щелкните **Запуск без отладки**.  
  
     Веб-форма будет запущена в Internet Explorer без присоединения отладчика.  
  
4.  Присоединитесь к процессу[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Дополнительные сведения см. в разделе [Отладка развернутых веб-приложений](../debugger/debugging-deployed-web-applications.md).  
  
5.  Нажмите кнопку в форме в обозревателе Internet Explorer.  
  
     В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] при этом должен произойти переход на точку останова на странице кода Default.aspx.cs, Default.aspx.vb или Default.aspx.  
  
6.  По завершении отладки в **Отладка** меню, щелкните **остановить отладку**.  
  
## <a name="see-also"></a>См. также  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)



