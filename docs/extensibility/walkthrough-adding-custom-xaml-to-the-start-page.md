---
title: "Пошаговое руководство: Добавление пользовательского XAML-файла начальной страницы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c19658e44daf96b6db96c503de1b59127b673111
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Пошаговое руководство: Добавление пользовательского XAML-файла начальной страницы
В этом пошаговом руководстве демонстрируется создание настраиваемого начальной страницы Visual Studio, содержащий веб-браузера.  
  
## <a name="adding-custom-xaml"></a>Добавление пользовательского XAML-файла  
  
1.  Создание домашней страницы, следуя инструкциям в разделе [Создание начальной страницы пользовательских](../extensibility/creating-a-custom-start-page.md).  
  
2.  Найдите в файле MainWindow.xaml \<Сетка настроек раздела.  
  
3.  Добавить \<TabControl настроек элемента и \<TabItem настроек внутри \< Сетка настроек элемента, как показано в следующем примере.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Добавьте второй \<TabItem настроек, с \<кнопку настроек элемент, который открывает новый проект:  
  
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
  
     Откроется экспериментальный экземпляр Visual Studio, пользовательские начальная страница установки, но не выбраны.  
  
2.  В экспериментальном экземпляре Visual Studio, откройте **Tools/Options / среды** страницы.  
  
3.  Выберите **запуска**. На **настроить начальную страницу** выберите XAML-файле, а затем нажмите **ОК**.  
  
4.  В меню **Вид** выберите пункт **Начальная страница**.  
  
5.  Щелкните **Bing** вкладки.  
  
     Вы увидите веб-страницу Bing.  
  
6.  Щелкните **MyButton** вкладки.  
  
     Вы должны увидеть **MyProject** кнопку, чтобы открыть **новый проект** диалогового окна.  
  
7.  Закройте экспериментальный экземпляр.  
  
## <a name="applying-the-custom-start-page"></a>Применение настраиваемой начальной страницы  
  
#### <a name="to-test-the-custom-start-page"></a>Для проверки пользовательских начальной страницы  
  
1.  В **Сервис / Параметры / Среда**выберите **запуска**. На **настроить начальную страницу** выберите XAML-файле, а затем нажмите **ОК**.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 На начальной странице Visual Studio теперь содержит вкладку, которая отображает вкладку веб-браузера и вкладка MyButton. Можно создавать настраиваемые начальные страницы с другими функциями с помощью *кода* модели, чтобы добавить пользовательские DLL-файлы, как показано в [Добавление пользовательского элемента управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md). Настраиваемые начальные страницы можно совместно с другими пользователями путем публикации полученный VSIX-файл для [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) веб-сайт или другой веб-сайт или сеть для совместного использования. Дополнительные сведения см. в разделе [развертывание пользовательских начинать создание страниц](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Контейнерные элементы управления WPF](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)
