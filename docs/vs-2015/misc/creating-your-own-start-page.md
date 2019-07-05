---
title: Создание собственной начальной страницы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: cc465ca5bc9474aaba51042d453a57ee7ec124ec
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432303"
---
# <a name="creating-your-own-start-page"></a>Создание собственной начальной страницы
Настраиваемую начальную страницу можно создать с помощью шаблона проекта начальной страницы или путем создания пустой начальной страницы.  
  
 В конструкторе XAML визуальные представления настраиваемых начальных страниц могут быть не абсолютно точными из-за зависимостей от модели приложения Visual Studio.  
  
## <a name="using-the-project-template"></a>Использование шаблона проекта  
 Шаблон проекта начальной страницы создает проект начальной страницы, который представляет собой полную копию начальной страницы Visual Studio. После этого вы можете изменить начальную страницу согласно своим требованиям.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Создание настраиваемой начальной страницы с помощью шаблона проекта начальной страницы  
  
1. Скачайте и установите [шаблон проекта начальной страницы](http://go.microsoft.com/fwlink/?LinkId=186204) из коллекции Visual Studio.  
  
    > [!WARNING]
    > На данный момент шаблон проекта начальной страницы Visual Studio 2010 еще не обновлен. Сведения об обновлении этого шаблона см. в разделе [как: Обновление настраиваемой начальной страницы Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Установив шаблон, создайте с его помощью проект начальной страницы.  
  
3. В левой области диалогового окна "Создание проекта" в разделе **Установленные шаблоны**разверните узел **Другие типы проектов** , а затем щелкните **Расширяемость**.  
  
4. В средней области выберите **Настраиваемая начальная страница**, укажите имя проекта и нажмите кнопку **ОК**.  
  
     Среда Visual Studio создаст проект начальной страницы, который представляет собой полную копию начальной страницы Visual Studio.  
  
5. В **обозревателе решений**откройте файл **StartPage.xaml**.  
  
6. Отредактируйте файл StartPage.xaml.  
  
     Чтобы просмотреть результаты работы, можно нажать клавишу F5, чтобы открыть экспериментальный экземпляр Visual Studio с установленной настраиваемой начальной страницей.  
  
## <a name="creating-a-blank-start-page"></a>Создание пустой начальной страницы  
 Самый простой способ создать пустую начальную страницу — воспользоваться шаблоном проекта начальной страницы, а затем удалить содержимое.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Создание пустой начальной страницы с помощью шаблона проекта начальной страницы  
  
1. Создайте проект начальной страницы с помощью шаблона проекта начальной страницы, как описано в предыдущей процедуре.  
  
2. Откройте файл StartPage.xaml.  
  
3. Удалите все содержимое страницы, оставив только внешние элементы XML и содержащий элемент сетки <xref:System.Windows.Controls.Grid>. В результате XAML-файл должен выглядеть так, как показано в примере ниже.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Удалите все вспомогательные файлы, которые вы не планируете использовать.  
  
    Файлы VSIX и PKGDEF следует сохранить для целей развертывания.  
  
   Кроме того, пустую начальную страницу можно создать путем создания XAML-файла с правильной структурой тегов, распознаваемой средой Visual Studio. Затем можно добавить разметку и код программной части для получения нужного внешнего вида и функциональности. Дополнительные сведения см. в разделе [Создание настраиваемая начальная страница](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Тестирование и применение настраиваемой начальной страницы  
 Не запускайте начальную страницу в основном экземпляре, пока не убедитесь в том, что она работает без сбоев. Протестировав настраиваемую начальную страницу, можно применить ее к системе, повторив последние три действия этой процедуры в основном экземпляре Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Тестирование настраиваемой начальной страницы  
  
1. Нажмите клавишу F5.  
  
    Откроется экспериментальный экземпляр Visual Studio, в котором новая начальная страница установлена, но не выбрана.  
  
2. В экспериментальном экземпляре Visual Studio в меню **Сервис** выберите пункт **Параметры**.  
  
3. В диалоговом окне **Параметры** в разделе **Среда**выберите **Запуск**. Затем в списке **Настройка начальной страницы** выберите свой файл XAML и нажмите кнопку **ОК**.  
  
4. В меню **Вид** выберите пункт **Начальная страница**.  
  
    Откроется работающая начальная страница. Чтобы увидеть изменения, необходимо закрыть экспериментальный экземпляр, повторно скопировать все измененные файлы, а затем снова открыть экспериментальный экземпляр.  
  
   Вы можете делиться к настраиваемой начальной странице, отправьте файл VSIX из каталога bin\debug на [Visual Studio Marketplace](https://marketplace.visualstudio.com/) веб-сайт или на другой веб-сайт или интрасети в общую папку. Для получения дополнительной информации см. [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка начальной страницы](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Пошаговое руководство: добавление настраиваемого XAML-файла на начальную страницу](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)