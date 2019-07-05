---
title: Пошаговое руководство. Добавление пользовательского XAML начальную страницу | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674114"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Пошаговое руководство. Добавление настраиваемого XAML-файла на начальную страницу
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве демонстрируется создание настраиваемой Visual Studio начальной страницы, содержащий веб-браузер.  
  
## <a name="adding-custom-xaml"></a>Добавление пользовательского XAML  
  
1. Создание начальной страницы, следуя инструкциям в [Создание настраиваемая начальная страница](../extensibility/creating-a-custom-start-page.md).  
  
2. Найдите в файле MainWindow.xaml \<сетки > раздела.  
  
3. Добавить \<TabControl > элемент и \<TabItem > внутри \< сетки > элемента, как показано в следующем примере.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. Добавьте второй \<TabItem >, с помощью \<кнопку > элемент, который открывает новый проект:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Тестирование настраиваемой начальной страницы  
  
1. Нажмите клавишу F5.  
  
     Откроется экспериментальный экземпляр Visual Studio, настраиваемая начальная страница установлена, но не выбраны.  
  
2. В экспериментальном экземпляре Visual Studio, откройте **Tools/Options / среды** страницы.  
  
3. Выберите **запуска**. На **настроить начальную страницу** выберите свой файл XAML, а затем нажмите **ОК**.  
  
4. В меню **Вид** выберите пункт **Начальная страница**.  
  
5. Нажмите кнопку **Bing** вкладки.  
  
     Вы увидите веб-странице Bing.  
  
6. Нажмите кнопку **MyButton** вкладки.  
  
     Вы должны увидеть **MyProject** кнопку, чтобы открыть **новый проект** диалоговое окно.  
  
7. Закройте экспериментальный экземпляр.  
  
## <a name="applying-the-custom-start-page"></a>Применение настраиваемой начальной страницы  
  
#### <a name="to-test-the-custom-start-page"></a>Для тестирования настраиваемой начальной страницы  
  
1. В **Сервис / Параметры / Среда**выберите **запуска**. На **настроить начальную страницу** выберите свой файл XAML, а затем нажмите **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
 На начальной странице Visual Studio теперь содержит вкладку, которая отображает вкладку веб-браузера и MyButton вкладки. Можно создать настраиваемые начальные страницы с другими функциями с помощью *кода* модели для добавления настраиваемой библиотеки DLL, как показано в [Добавление пользовательского элемента управления на начальной странице](../extensibility/adding-user-control-to-the-start-page.md). Настраиваемые начальные страницы можно поделиться с другими пользователями путем публикации полученный файл .vsix в [Visual Studio Marketplace](https://marketplace.visualstudio.com/) веб-сайт или на другой веб-сайт или сети в общую папку. Для получения дополнительной информации см. [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Контейнерные элементы управления WPF](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
