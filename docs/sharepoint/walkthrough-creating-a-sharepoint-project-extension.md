---
title: Пошаговое руководство. Создание расширения проекта SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fd142b71de2919f1f44f36134ce286e58229bae5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866117"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Пошаговое руководство. Создание расширения проекта SharePoint
  В этом пошаговом руководстве показано, как создавать расширения для проектов SharePoint. Можно использовать расширение проекта реагировать на события уровня проекта, например при проект добавлен, удален или переименован. Также можно добавлять пользовательские свойства или ответное действие при изменении значения свойства. В отличие от расширений элемента проекта расширения проекта нельзя связать с определенным типом проекта SharePoint. При создании расширения проекта, расширение загружается при открытии любого проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 В этом пошаговом руководстве вы создадите пользовательский логическое свойство, которое добавляется в любой проект SharePoint, созданные в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Если задано значение **True**, добавляет новое свойство или сопоставляет с ним папку ресурсов изображений в проект. Если задано значение **False**, папка "изображения" удаляется, если он существует. Дополнительные сведения см. в разделе [как: Добавление и удаление сопоставленных папок](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] расширения для проектов SharePoint, выполняющий следующие:  
  
    -   Добавляет настраиваемое свойство проекта в окне «Свойства». Свойство применяется к любому проекту SharePoint.  
  
    -   Использует объектную модель проекта SharePoint, Добавление сопоставленной папки в проект.  
  
    -   Использует [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] объектной модели автоматизации (DTE), чтобы удалить сопоставленную папку из проекта.  
  
-   Построение [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакета Extension (VSIX) для развертывания сборки расширения свойств проекта.  
  
-   Отладка и тестирование свойства проекта.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимы следующие компоненты на компьютере разработчика для выполнения этого пошагового руководства.  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint и [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. В этом пошаговом руководстве использует **проект VSIX** шаблона в [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] Создание пакета VSIX для развертывания расширения свойства проекта. Дополнительные сведения см. в разделе [расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="create-the-projects"></a>Создание проектов
 Для выполнения этого пошагового руководства, необходимо создать два проекта:  
  
- Проект VSIX, чтобы создать пакет VSIX для развертывания расширения проекта.  
  
- Проект библиотеки классов, реализующий расширение проекта.  
  
  Начало выполнения пошагового руководства по созданию проектов.  
  
#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
3.  В **новый проект** диалогового окна разверните узел **Visual C#** или **Visual Basic** узлов и нажмите кнопку **расширяемости** узла.  
  
    > [!NOTE]  
    >  Этот узел доступен только в том случае, если установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом разделе.  
  
4.  В верхней части диалоговое окно, выберите **.NET Framework 4.5** в списке версий .NET Framework, а затем выберите **проект VSIX** шаблона.  
  
5.  В **имя** введите **Пакет_расширений_проекта**, а затем выберите **ОК** кнопки.  
  
     **Пакет_расширений_проекта** проект появится в **обозревателе решений**.  
  
#### <a name="to-create-the-extension-project"></a>Создание проекта расширения  
  
1.  В **обозревателе решений**, откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В **новый проект** диалогового окна последовательно раскройте элементы **Visual C#** или **Visual Basic** узлов, а затем выберите **Windows**.  
  
3.  В верхней части диалоговое окно, выберите **.NET Framework 4.5** в списке версий .NET Framework, а затем выберите **библиотеки классов** шаблон проекта.  
  
4.  В **имя** введите **Расширение_проекта**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **Расширение_проекта** проекта в решение и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
## <a name="configure-the-project"></a>Настройка проекта
 Прежде чем писать код для создания расширения проекта, добавьте файлы кода и ссылки на сборки в проект расширения.  
  
#### <a name="to-configure-the-project"></a>Настройка проекта  
  
1.  Добавьте файл кода, который называется **CustomProperty** Расширение_проекта проект.  
  
2.  Откройте контекстное меню для **Расширение_проекта** проекта, а затем выберите **добавить ссылку**.  
  
3.  В **диспетчер ссылок - CustomProperty** диалоговое окно, выберите **Framework** узел, а затем выберите флажок рядом со сборками System.ComponentModel.Composition и System.Windows.Forms.  
  
4.  Выберите **расширения** узел, установите флажок рядом со сборками Microsoft.VisualStudio.SharePoint и EnvDTE, а затем выберите **ОК** кнопки.  
  
5.  В **обозревателе решений**в разделе **ссылки** папку для **Расширение_проекта** проекта, выберите **EnvDTE**.  
  
6.  В **свойства** измените **Embed Interop Types** свойства **False**.  
  
## <a name="define-the-new-sharepoint-project-property"></a>Определение нового свойства проекта SharePoint
 Создайте класс, который определяет расширение проекта и поведение нового свойства проекта. Чтобы определить новое расширение проекта, этот класс реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейс. Реализуйте этот интерфейс, каждый раз, когда требуется определить расширение для проекта SharePoint. Кроме того, добавьте <xref:System.ComponentModel.Composition.ExportAttribute> к классу. Этот атрибут позволяет [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] обнаружить и загрузить вашей <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализации. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> конструктору атрибута тип.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Чтобы определить новое свойство проекта SharePoint  
  
1.  Вставьте следующий код в файле кода CustomProperty.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>Построение решения
 Затем выполнить сборку решения, чтобы убедиться в том, что оно компилируется без ошибок.  
  
#### <a name="to-build-the-solution"></a>Построение решения  
  
1.  В строке меню последовательно выберите **Сборка**  >  **Собрать решение**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Создание пакета VSIX для развертывания расширения свойства проекта
 Чтобы развернуть расширение проекта, используйте проекта VSIX в решении для создания пакета VSIX. Во-первых настройте пакет VSIX, изменив файл source.extension.vsixmanifest, включенный в проект VSIX. Затем создайте пакет VSIX, построения решения.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Настройка и создание пакета VSIX  
  
1.  В **обозревателе решений**, откройте контекстное меню для файла source.extension.vsixmanifest и затем выберите **откройте** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Открывает файл в конструкторе манифеста. Сведения, отображаемые в **метаданных** также отображается вкладка **расширения и обновления**. Все пакеты VSIX требуется файл extension.vsixmanifest. Дополнительные сведения об этом файле см. в разделе [Справочник по схеме 1.0 VSIX расширения](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В **название продукта** введите **настраиваемое свойство проекта**.  
  
3.  В **автор** введите **Contoso**.  
  
4.  В **описание** введите **настраиваемое свойство проекта SharePoint, который переключает сопоставление в папке ресурсов изображений в проект**.  
  
5.  Выберите **активы** вкладке, а затем выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
6.  В **тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует `MEFComponent` элемент в файл extension.vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  В **источника** выберите **проект в текущем решении** переключатель.  
  
8.  В **проекта** выберите **Расширение_проекта**.  
  
     Это значение определяет имя сборки, которое вы создаете в проекте.  
  
9. Выберите **ОК** закрыть **добавить новый актив** диалоговое окно.  
  
10. В строке меню выберите **файл** > **сохранить все** при завершении, а затем закройте конструктор манифеста.  
  
11. В строке меню выберите **построения** > **построить решение**и убедитесь, что проект компилируется без ошибок.  
  
12. В **обозревателе решений**, откройте контекстное меню для **Пакет_расширений_проекта** проекта и выберите **открыть папку в проводнике** кнопки.  
  
13. В **проводнике**, откройте выходную папку построения для проекта Пакет_расширений_проекта и убедитесь, что папка содержит файл с именем Пакет_расширений_проекта.VSIX.  
  
     По умолчанию является выходной папке сборки... папку \bin\debug в папке, содержащей файл проекта.  
  
## <a name="test-the-project-property"></a>Проверка свойства проекта
 Теперь вы готовы к тестированию настраиваемое свойство проекта. Проще всего отладка и тестирование новое расширение свойства проекта в экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Этот экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создается при запуске VSIX или другого проекта расширения. Завершив отладку проекта, можно установить расширение на компьютер и затем продолжить отладку и тестирование в обычном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Отладка и тестирование расширения в экспериментальном экземпляре Visual Studio  
  
1.  Перезапустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора, а затем откройте решение "Пакет_расширений_проекта".  
  
2.  Запустите отладочную сборку проекта, выбрав **F5** ключа или в строке меню выберите **Отладка** > **начать отладку**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 проекта и запускает экспериментальный экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  В экспериментальном экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], создайте проект для решения фермы SharePoint и использовать значения по умолчанию для других значений в мастере.  
  
    1.  В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
    2.  В верхней части **новый проект** диалоговое окно, выберите **.NET Framework 3.5** в списке версий .NET Framework.  
  
         Расширения инструментов SharePoint требуются функции в этой версии [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  В разделе **шаблоны** узел, разверните **Visual C#** или **Visual Basic** узел, выберите **SharePoint** узел и нажмите кнопку **2010** узла.  
  
    4.  Выберите **проект SharePoint 2010** шаблона, а затем введите **ModuleTest** как имя проекта.  
  
4.  В **обозревателе решений**, выберите **ModuleTest** узел проекта.  
  
     Новое пользовательское свойство **сопоставить папку изображений** отображается в **свойства** окно со значением по умолчанию **False**.  
  
5.  Измените значение этого свойства для **True**.  
  
     Папка ресурсов изображения добавляется в проект SharePoint.  
  
6.  Верните значение этого свойства **False**.  
  
     При выборе **Да** кнопку **удалите папку образов?** диалоговое окно, изображения, папка ресурсов удаляется из проекта SharePoint.  
  
7.  Закройте экспериментальный образец [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также
 [Расширение проектов SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Практическое руководство. Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Связывать пользовательские данные с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
