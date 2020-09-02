---
title: Пошаговое руководство. Добавление пользовательского XAML-кода на начальную страницу | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674114"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Пошаговое руководство. Добавление настраиваемого XAML-файла на начальную страницу
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как создать настраиваемую начальную страницу Visual Studio, содержащую веб-браузер.  
  
## <a name="adding-custom-xaml"></a>Добавление пользовательского XAML  
  
1. Создайте начальную страницу, следуя инструкциям в разделе [Создание настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md).  
  
2. В файле MainWindow. XAML найдите \<Grid> раздел.  
  
3. Добавьте \<TabControl> элемент и \<TabItem> внутрь \< Grid> элемента, как показано в следующем примере.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. Добавьте второй \<TabItem> \<Button> элемент с элементом, открывающим новый проект:  
  
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
  
     Откроется экспериментальный экземпляр Visual Studio с установленным пользовательским начальным окном, но не выбранным.  
  
2. В экспериментальном экземпляре Visual Studio откройте страницу **инструменты/Options/среда** .  
  
3. Выберите **Запуск**. В списке **Настройка начальной страницы** выберите свой XAML-файл и нажмите кнопку **ОК**.  
  
4. В меню **Вид** выберите пункт **Начальная страница**.  
  
5. Перейдите на вкладку **Bing** .  
  
     Вы должны увидеть веб-страницу Bing.  
  
6. Перейдите на вкладку **MyButton** .  
  
     Вы должны увидеть кнопку **MyProject** , которая открывает диалоговое окно **Новый проект** .  
  
7. Закройте экспериментальный экземпляр.  
  
## <a name="applying-the-custom-start-page"></a>Применение настраиваемой начальной страницы  
  
#### <a name="to-test-the-custom-start-page"></a>Тестирование настраиваемой начальной страницы  
  
1. В **меню Сервис/параметры/среда**выберите **Запуск**. В списке **Настройка начальной страницы** выберите свой XAML-файл и нажмите кнопку **ОК**.  
  
## <a name="next-steps"></a>Next Steps  
 Теперь начальная страница Visual Studio содержит вкладку, в которой отображается вкладка веб-браузер и вкладка MyButton. Можно создать пользовательские начальные страницы с другими функциями с помощью модели *кода программной части* , чтобы добавить пользовательскую библиотеку DLL, как показано в статье [Добавление пользовательского элемента управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md). Пользовательские начальные страницы можно совместно использовать с другими пользователями, публикуя полученный VSIX-файл на [Visual Studio Marketplaceм](https://marketplace.visualstudio.com/) сайте или на другом веб-сайте или в сетевой папке. Для получения дополнительной информации см. [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Элементы управления контейнера WPF](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
