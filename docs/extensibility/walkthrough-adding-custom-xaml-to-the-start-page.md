---
title: Пошаговое руководство. Добавление пользовательского XAML начальную страницу | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a828fe6f7944e2bb0d9527d781c66630ed1f3879
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947287"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Пошаговое руководство. Добавление пользовательского XAML на начальную страницу
В этом пошаговом руководстве демонстрируется создание настраиваемой Visual Studio начальной страницы, содержащий веб-браузер.  
  
## <a name="adding-custom-xaml"></a>Добавление пользовательского XAML  
  
1.  Создание начальной страницы, следуя инструкциям в [Создание настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md).  
  
2.  В *MainWindow.xaml* найдите \<сетки > раздела.  
  
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
  
4.  Добавьте второй \<TabItem >, с помощью \<кнопку > элемент, который открывает новый проект:  
  
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
  
1.  Нажмите клавишу **F5**.  
  
     Откроется экспериментальный экземпляр Visual Studio, настраиваемая начальная страница установлена, но не выбраны.  
  
2.  В экспериментальном экземпляре Visual Studio, откройте **Tools/Options / среды** страницы.  
  
3.  Выберите **запуска**. На **настроить начальную страницу** выберите ваш *.xaml* файла и нажмите кнопку **ОК**.  
  
4.  В меню **Вид** выберите пункт **Начальная страница**.  
  
5.  Нажмите кнопку **Bing** вкладки.  
  
     Вы увидите веб-странице Bing.  
  
6.  Нажмите кнопку **MyButton** вкладки.  
  
     Вы должны увидеть **MyProject** кнопку, чтобы открыть **новый проект** диалоговое окно.  
  
7.  Закройте экспериментальный экземпляр.  
  
## <a name="apply-the-custom-start-page"></a>Применение настраиваемой начальной страницы  
  
### <a name="to-test-the-custom-start-page"></a>Для тестирования настраиваемой начальной страницы  
  
1.  В **Сервис / Параметры / Среда**выберите **запуска**. На **настроить начальную страницу** выберите ваш *.xaml* файла и нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Следующие шаги  
 На начальной странице Visual Studio теперь содержит вкладку, которая отображает вкладку веб-браузера и MyButton вкладки. Можно создать настраиваемые начальные страницы с другими функциями с помощью *кода* модели для добавления настраиваемой библиотеки DLL, как показано в [Добавление пользовательского элемента управления на начальной странице](../extensibility/adding-user-control-to-the-start-page.md). Настраиваемые начальные страницы можно поделиться с другими пользователями путем публикации полученный файл .vsix в [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) веб-сайт или на другой веб-сайт или сети в общую папку. Для получения дополнительной информации см. [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Контейнерные элементы управления WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)