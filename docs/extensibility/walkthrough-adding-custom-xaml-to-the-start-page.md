---
title: 'Пошаговое руководство: Добавление пользовательского XAML-файла начальной страницы | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e6e782e703282f9eb4e189671c086eb17db427
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Пошаговое руководство: Добавление пользовательского XAML-файла начальной страницы
В этом пошаговом руководстве демонстрируется создание пользовательского начальной страницы Visual Studio, содержащий веб-браузер.  
  
## <a name="adding-custom-xaml"></a>Добавление пользовательского XAML  
  
1.  Создание начальной страницы в соответствии с инструкциями в [Создание настраиваемая начальная страница](../extensibility/creating-a-custom-start-page.md).  
  
2.  Найдите в файле MainWindow.xaml \<сетки > раздела.  
  
3.  Добавить \<TabControl > элемент и \<TabItem > внутри \< сетки > элемента, как показано в следующем примере.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Добавьте второй \<TabItem >, с \<кнопку > элемент, который открывает новый проект:  
  
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
  
1.  Нажмите клавишу F5.  
  
     Откроется экспериментальный экземпляр Visual Studio, настраиваемая начальная страница установлена, но не выбраны.  
  
2.  В экспериментальном экземпляре Visual Studio, откройте **Tools/Options / среды** страницы.  
  
3.  Выберите **запуска**. На **настроить начальную страницу** выберите свой файл XAML, а затем нажмите **ОК**.  
  
4.  В меню **Вид** выберите пункт **Начальная страница**.  
  
5.  Нажмите кнопку **Bing** вкладки.  
  
     Вы увидите Bing веб-страницы.  
  
6.  Нажмите кнопку **MyButton** вкладки.  
  
     Вы увидите **MyProject** кнопку, чтобы открыть **новый проект** диалогового окна.  
  
7.  Закройте экспериментальный экземпляр.  
  
## <a name="applying-the-custom-start-page"></a>Применение настраиваемой начальной страницы  
  
#### <a name="to-test-the-custom-start-page"></a>Тестирование настраиваемой начальной страницы  
  
1.  В **Сервис / Параметры / Среда**выберите **запуска**. На **настроить начальную страницу** выберите свой файл XAML, а затем нажмите **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
 На начальной странице Visual Studio теперь содержит вкладку, которая отображает вкладку веб-браузера и MyButton вкладки. Можно создавать настраиваемые начальные страницы с другими функциями с помощью *кода* модели, чтобы добавить пользовательские DLL-файлы, как показано в [Добавление пользовательского элемента управления на начальной странице](../extensibility/adding-user-control-to-the-start-page.md). Настраиваемые начальные страницы можно предоставить доступ другим пользователям путем публикации полученный VSIX-файл для [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) веб-сайт или другой веб-сайт или сети для совместного использования. Дополнительные сведения см. в разделе [развертывание пользовательских начальные страницы](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Контейнерные элементы управления WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)