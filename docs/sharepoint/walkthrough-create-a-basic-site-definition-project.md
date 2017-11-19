---
title: "Пошаговое руководство: Создание базового проекта определения сайта | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: b0df5b0e-5fa0-43d8-a339-6d92f1276764
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9bea8fec27b0d53fb1cfe3405d39d271a93f5a8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Пошаговое руководство. Создание базового проекта определения сайта
  В этом пошаговом руководстве демонстрируется создание простейшего определения сайта, содержащий Визуальная веб-часть с некоторыми элементами управления, на нем. Для ясности визуальной веб-части, создаваемом имеет несколько элементов управления. Тем не менее можно создать более сложное определений сайтов SharePoint, которые включают дополнительные функциональные возможности.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание определения сайта с помощью [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] шаблона проекта.  
  
-   Создание сайта SharePoint с помощью нового определения сайта в SharePoint.  
  
-   Добавление визуальной веб-части в решение.  
  
-   Настройка страницы сайта default.aspx путем добавления визуальной веб-части в него.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые редакции Microsoft Windows и SharePoint. Дополнительные сведения см. в разделе Требования к разработке решений SharePoint.  
  
-   Visual Studio.  
  
## <a name="creating-a-site-definition-solution"></a>Создание решения определения сайта  
 Во-первых, Создание проекта определения сайта в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-create-a-site-definition-project"></a>Создание проекта определения сайта  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**. Если интерфейс IDE настроен на использование параметров разработки Visual Basic, в строке меню, выберите **файл**, **новый проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2.  Разверните **Visual C#** узел или **Visual Basic** узел, разверните **SharePoint** узел и выберите **2010** узла.  
  
3.  В **шаблоны** выберите **проект SharePoint 2010** шаблона.  
  
4.  В **имя** введите **TestSiteDef**, а затем выберите **ОК** кнопки.  
  
     **Мастер настройки SharePoint** отображается.  
  
5.  На **Укажите сайт и уровень безопасности для отладки** введите URL-адрес для сайта SharePoint, где будет выполняться отладка определения сайта или использовать расположение по умолчанию (http://*системное имя*/).  
  
6.  В **Какова степень доверия для этого решения SharePoint?** выберите **развернуть как решение фермы** переключатель.  
  
     Все проекты определений сайтов необходимо развертывать как решения фермы. Дополнительные сведения об изолированных решениях и решений фермы см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Выберите **Готово** кнопки.  
  
     Проект отображается в **обозревателе решений**.  
  
8.  В **обозревателе решений**, выберите узел проекта и затем в строке меню выберите **проекта**, **Добавление нового элемента**.  
  
9. В рамках одного **Visual C#** или **Visual Basic**, разверните **SharePoint** узла, а затем выберите **2010** узла.  
  
10. В **шаблоны** области, выберите **определения сайта** шаблона, оставьте **имя** как **SiteDefinition1**и нажмите кнопку  **Добавить** кнопки.  
  
## <a name="create-a-visual-web-part"></a>Создание визуальной веб-части  
 Теперь необходимо создать визуальную веб-часть, отображаемую на главной странице определения сайта.  
  
#### <a name="to-create-a-visual-web-part"></a>Для создания визуальной веб-части  
  
1.  В **обозревателе решений**, выберите **Показать все файлы** кнопки.  
  
2.  Выберите **SiteDefinition1** узел проекта, а затем в строке меню выберите **проекта**, **Добавление нового элемента**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
3.  Разверните **Visual C#** узел или **Visual Basic** узел, разверните **SharePoint** узел и выберите **2010** узла.  
  
4.  В списке шаблонов выберите **визуальной веб-части** шаблона, сохраните значение по умолчанию имя VisualWebPart1 и нажмите кнопку **добавить** кнопки.  
  
     Будет открыт файл VisualWebPart1.ascx.  
  
5.  В конце файла VisualWebPart1.ascx добавьте следующую разметку, чтобы добавить в форму три элемента управления: текстовое поле, кнопку и метку:  
  
    ```  
    <table>  
      <tr>  
        <td>  
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>  
        </td>  
        <td>  
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>  
        </td>  
        <td>  
          <asp:Label runat="server" ID="lblName"></asp:Label>  
        </td>  
      </tr>  
    </table>  
    ```  
  
6.  Откройте файл VisualWebPart1.ascx.cs (для [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) или VisualWebPart1.ascx.vb (для [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) и добавьте следующий код:  
  
     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
     Этот код добавляет функцию нажатия кнопки веб-части.  
  
## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Добавление визуальной веб-части на страницу Default.aspx.  
 Затем добавьте визуальной веб-части определения сайта по умолчанию ASPX-страницу.  
  
#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Добавление визуальной веб-части на страницу Default.aspx.  
  
1.  Откройте страницу default.aspx и добавьте следующую строку после тега `WebPartPages`:  
  
    ```  
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>  
    ```  
  
     Эта строка связывает имя MyWebPartControls с веб-части и его код. *Имен* соответствует пространству имен, который используется в файле кода VisualWebPart1.ascx.  
  
2.  Найдите элемент `</asp:Content>` и замените весь последующий раздел `ContentPlaceHolderId="PlaceHolderMain"` и его содержимое следующим кодом.  
  
    ```  
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">  
        <MyWebPartControls:VisualWebPart1 runat="server" />      
    </asp:Content>  
    ```  
  
     Этот код создает ссылку на визуальной веб-части, которое было создано ранее.  
  
3.  В **обозревателе решений**, откройте контекстное меню для **SiteDefinition1** узел, а затем выберите **назначить автозапускаемым элементом**.  
  
## <a name="deploy-and-run-the-site-definition-solution"></a>Развертывание и запуск решения определения сайта  
 Далее, разверните проект в SharePoint, а затем запустите проект.  
  
#### <a name="to-deploy-and-run-the-site-definition"></a>Развертывание и запуск определения сайта  
  
-   В строке меню выберите **построения**, **развертывание TestSiteDef**.  
  
-   Нажмите клавишу F5.  
  
     Visual Studio скомпилирует код, добавит его компоненты, поместит все его файлы в WSP-файл пакета и развернет этот WSP-файл на сервере SharePoint. SharePoint, затем устанавливает файлы, а затем активирует возможности.  
  
## <a name="create-a-site-based-on-the-site-definition"></a>Создайте сайт на основе определения сайта  
 Создайте сайт с помощью нового определения сайта.  
  
#### <a name="to-create-a-site-by-using-the-site-definition"></a>Чтобы создать сайт с помощью определения сайта  
  
1.  На сайте SharePoint появится страница новый сайт SharePoint.  
  
2.  В **название и описание** введите **My New Site** заголовок и описание узла.  
  
3.  В **адреса веб-сайта** введите **новый_узел** в **URL-имя** поле.  
  
4.  В **шаблона** выберите **пользовательские разработки SharePoint** вкладки.  
  
5.  В **выберите шаблон** выберите **SiteDefinition1**.  
  
6.  Для остальных параметров оставьте значения по умолчанию, а затем выберите **создать** кнопки.  
  
     Появится новый сайт.  
  
## <a name="test-the-new-site"></a>Тестирование нового сайта  
 Теперь необходимо протестировать работу созданного сайта.  
  
#### <a name="to-test-the-new-site"></a>Чтобы протестировать работу созданного сайта  
  
-   На странице Default.aspx, введите текст и выберите **измените текст надписи** кнопку рядом с текстовым полем.  
  
     Текст отобразится на метке справа от кнопки.  
  
## <a name="see-also"></a>См. также  
 [Как: Создание приемника событий](../sharepoint/how-to-create-an-event-receiver.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  