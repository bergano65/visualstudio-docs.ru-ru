---
title: Пошаговое руководство. Создание базового проекта определения сайта | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 078fcc4d30613e4fe19b493150ce4570196b73ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608881"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Пошаговое руководство. Создание базового проекта определения сайта
  В этом пошаговом руководстве демонстрируется создание простейшего определения сайта, содержащий визуальной веб-части, с некоторыми элементами управления на нем. Ради ясности визуальной веб-части, созданной имеет несколько элементов управления. Тем не менее можно создать более сложные определений сайтов SharePoint, которые включают дополнительные функции.

 В этом пошаговом руководстве описаны следующие задачи.

- Создание определения сайта с помощью [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] шаблона проекта.

- Создание на сайте SharePoint с помощью определения сайта в SharePoint.

- Добавление визуальной веб-части в решение.

- Настройка страницы default.aspx веб-узла путем добавления визуальной веб-части в него.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

-   Поддерживаемые редакции Microsoft Windows и SharePoint. Дополнительные сведения см. в разделе Требования к разработке решений SharePoint.

-   Visual Studio.

## <a name="create-a-site-definition-solution"></a>Создание решения определения сайта
 Во-первых, Создание проекта определения сайта в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

#### <a name="to-create-a-site-definition-project"></a>Создание проекта определения сайта

1. В строке меню выберите **Файл** > **Создать** > **Проект**. Если интерфейс IDE настроен на использование параметров разработки Visual Basic, в строке меню, выберите **файл** > **новый проект**.

    Откроется диалоговое окно **Новый проект** .

2. Разверните **Visual C#** узел или **Visual Basic** узел, разверните **SharePoint** узел и нажмите кнопку **2010** узла.

3. В **шаблоны** выберите **проект SharePoint 2010** шаблона.

4. В **имя** введите **TestSiteDef**, а затем выберите **ОК** кнопки.

    **Мастер настройки SharePoint** отображается.

5. На **Укажите сайт и уровень безопасности для отладки** странице, введите URL-адрес сайта SharePoint, где будет выполняться отладка определения сайта или используйте расположение по умолчанию (http://<em>системное имя</em>/).

6. В **Какова степень доверия для этого решения SharePoint?** выберите **развернуть как решение фермы** переключатель.

    Все проекты определений сайтов должны быть развернуты как решения фермы. Дополнительные сведения об изолированных решениях и решений фермы см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).

7. Выберите **Готово** кнопки.

    Проект отображается в **обозревателе решений**.

8. В **обозревателе решений**, выберите узел проекта и затем в строке меню выберите **проекта** > **Добавление нового элемента**.

9. В группе **Visual C#** или **Visual Basic**, разверните **SharePoint** узел, а затем выберите **2010** узла.

10. В **шаблоны** области выберите **определения сайта** шаблона, оставьте **имя** как **SiteDefinition1**, а затем выберите  **Добавление** кнопки.

## <a name="create-a-visual-web-part"></a>Создание визуальной веб-части
 Теперь необходимо создать визуальную веб-часть, отображаемую на главной странице определения сайта.

#### <a name="to-create-a-visual-web-part"></a>Для создания визуальной веб-части

1.  В **обозревателе решений**, выберите **Показать все файлы** кнопки.

2.  Выберите **SiteDefinition1** узел проекта, а затем в строке меню выберите **проекта** > **Добавление нового элемента**.

     Откроется диалоговое окно **Добавление нового элемента**.

3.  Разверните **Visual C#** узел или **Visual Basic** узел, разверните **SharePoint** узел и нажмите кнопку **2010** узла.

4.  В списке шаблонов выберите **визуальной веб-части** шаблона, сохраните значение по умолчанию назовите VisualWebPart1, а затем нажмите **добавить** кнопки.

     *VisualWebPart1.ascx* файл открывается.

5.  В нижней части *VisualWebPart1.ascx*, добавьте следующую разметку для добавления в форму три элемента управления: текстовое поле, кнопку и метку:

    ```aspx-csharp
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

6.  В разделе *VisualWebPart1.ascx*откройте *VisualWebPart1.ascx.cs* файла (для [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) или *VisualWebPart1.ascx.vb* (для [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), а затем добавьте Следующий код:

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Этот код добавляет функциональные возможности для нажатия кнопки веб-части.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Добавление визуальной веб-части на страницу ASPX по умолчанию
 Затем добавьте визуальной веб-части на страницу ASPX по умолчанию определения сайта.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Добавление визуальной веб-части на страницу Default.aspx.

1.  Откройте страницу default.aspx и добавьте следующую строку после тега `WebPartPages`:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Эта строка связывает имя MyWebPartControls с веб-части и ее код. *Пространства имен* параметр соответствует пространство имен, которое используется в *VisualWebPart1.ascx* файл кода.

2.  Найдите элемент `</asp:Content>` и замените весь последующий раздел `ContentPlaceHolderId="PlaceHolderMain"` и его содержимое следующим кодом.

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Этот код создает ссылку на визуальной веб-части, который был создан ранее.

3.  В **обозревателе решений**, откройте контекстное меню для **SiteDefinition1** узел, а затем выберите **назначить автозапускаемым элементом**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Развертывание и запуск решения определения сайта
 Далее, разверните проект в SharePoint, а затем запустите проект.

#### <a name="to-deploy-and-run-the-site-definition"></a>Развертывание и запуск определения сайта

-   В строке меню выберите **построения** > **развертывание TestSiteDef**.

-   Нажмите клавишу **F5**.

     Visual Studio скомпилирует код, добавит его компоненты, поместит все его файлы в WSP-файл пакета и развернет этот WSP-файл на сервере SharePoint. SharePoint, затем устанавливает файлы, а затем активирует функции.

## <a name="create-a-site-based-on-the-site-definition"></a>Создание сайта на основе определения сайта
 Создайте сайт с помощью нового определения узла.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Чтобы создать сайт с помощью определения сайта

1.  На сайте SharePoint откроется окно нового сайта SharePoint.

2.  В **заголовок и описание** введите **мой новый сайт** заголовок и описание узла.

3.  В **адрес веб-сайта** введите **новый_узел** в **имя URL-адреса** поле.

4.  В **шаблона** выберите **пользовательские разработки SharePoint** вкладки.

5.  В **выберите шаблон** выберите **SiteDefinition1**.

6.  Для остальных параметров оставьте значения по умолчанию, а затем выберите **создать** кнопки.

     Откроется новый сайт.

## <a name="test-the-new-site"></a>Проверка нового узла
 Теперь необходимо протестировать работу созданного сайта.

#### <a name="to-test-the-new-site"></a>Для тестирования нового сайта

-   На странице ASPX по умолчанию, ввести некоторый текст и выберите **измените текст надписи** кнопку рядом с текстовым полем.

     Текст отобразится на метке справа от кнопки.

## <a name="see-also"></a>См. также
- [Практическое руководство. Создание приемника событий](../sharepoint/how-to-create-an-event-receiver.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
