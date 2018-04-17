---
title: 'Пошаговое руководство: Создание пользовательского загрузчика для отображения подсказки о конфиденциальности | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 6f20389e0487fd548ac239503faae01adb7dbdf1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>Пошаговое руководство. Создание пользовательского загрузчика для вывода окна с предупреждением о конфиденциальности
Можно настроить приложения ClickOnce для автоматического обновления при появлении сборок с более новой версии файла и версии сборки. Чтобы убедиться в том, что пользователи согласны на это поведение, можно отобразить окно подтверждения к ним. Затем их можно выбрать, следует ли предоставить приложению для автоматического обновления. Если приложение не может выполнять автоматическое обновление, не устанавливает.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Visual Studio 2010.  
  
## <a name="creating-an-update-consent-dialog-box"></a>Создание диалогового окна подтверждения обновления  
 Чтобы отобразить окно подтверждения, создайте приложение, запрашивающее у пользователя согласие на автоматическое обновление для приложения.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Создание диалогового окна подтверждения  
  
1.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
2.  В **новый проект** диалоговое окно, нажмите кнопку **Windows**, а затем нажмите кнопку **WindowsFormsApplication**.  
  
3.  Для **имя**, тип **ConsentDialog**, а затем нажмите кнопку **ОК**.  
  
4.  В конструкторе выберите форму.  
  
5.  В **свойства** измените **текст** свойства **Update Consent Dialog**.  
  
6.  В **элементов**, разверните **все формы Windows Forms**и перетащите **метка** на форму элемент управления.  
  
7.  В конструкторе щелкните элемент управления label.  
  
8.  В **свойства** измените **текст** свойства в разделе **внешний вид** следующее:  
  
     Приложение, которое вы собираетесь установить проверяет наличие последних обновлений в Интернете. Нажимая кнопку «Принимаю», вы разрешаете приложению, поиск и устанавливать обновления автоматически из Интернета.  
  
9. В **элементов**, перетащите **флажок** элемента управления в середину формы.  
  
10. В **свойства** измените **текст** свойства в разделе **макета** для **принимаю**.  
  
11. В **элементов**, перетащите **кнопку** элемента управления в левом нижнем углу формы.  
  
12. В **свойства** измените **текст** свойства в разделе **макета** для **Продолжение**.  
  
13. В **свойства** измените **(имя)** свойства в разделе **разработки** для **значение ProceedButton**.  
  
14. В **элементов**, перетащите **кнопку** элемента управления в правом нижнем углу формы.  
  
15. В **свойства** измените **текст** свойства в разделе **макета** для **отменить**.  
  
16. В **свойства** измените **(имя)** свойства в разделе **разработки** для **CancelButton**.  
  
17. В конструкторе, дважды щелкните **принимаю** флажок, чтобы создать обработчик события CheckedChanged.  
  
18. В файле кода Form1 добавьте следующий код в обработчик события CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Измените конструктор класса, чтобы отключить **Продолжение** кнопку по умолчанию.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. В файле кода Form1 добавьте следующий код для логической переменной для отслеживания, если конечный пользователь согласился им обновлений в Интернете.  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. В конструкторе, дважды щелкните **Продолжение** кнопку, чтобы создать обработчик события нажатия кнопки.  
  
22. В файле кода Form1 добавьте следующий код в обработчик событий Click для **Продолжение** кнопки.  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. В конструкторе, дважды щелкните **отменить** кнопку, чтобы создать обработчик события нажатия кнопки.  
  
24. В файле кода Form1 добавьте следующий код в обработчик событий Click для **отменить** кнопки.  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Обновление приложения будут возвращать ошибку, если пользователь соглашается не обновлений в Интернете.  
  
     Visual Basic только для разработчиков:  
  
    1.  В **обозревателе решений**, нажмите кнопку **ConsentDialog**.  
  
    2.  На **проекта** меню, нажмите кнопку **добавить модуль**, а затем нажмите кнопку **добавить**.  
  
    3.  В файле кода Module1.vb добавьте следующий код.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  На **проекта** меню, нажмите кнопку **Свойства ConsentDialog**, а затем нажмите кнопку **приложения** вкладку.  
  
    5.  Снимите флажок **Включить исполняющую среду**.  
  
    6.  В **автоматически запускаемый объект** раскрывающееся меню, выберите **Module1**.  
  
        > [!NOTE]
        >  Отключение исполняющей отключает функции, такие как визуальные стили Windows XP, события приложения, экрана-заставки, один экземпляр приложения и многое другое. Дополнительные сведения см. в разделе [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Для Visual C# для разработчиков:  
  
     Откройте файл кода Program.cs и добавьте следующий код.  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. На **построения** меню, нажмите кнопку **собрать решение**.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>Создание пользовательского пакета загрузчика  
 Чтобы отобразить окно подтверждения конечным пользователям, можно создать пользовательский пакет начального загрузчика для приложения Update Consent Dialog и включить его в качестве необходимого компонента во всех приложений ClickOnce.  
  
 Эта процедура демонстрирует создание настраиваемого пакета загрузчика путем создания в следующих документах:  
  
-   Файл для описания содержимого загрузчика манифеста product.xml.  
  
-   Чтобы вывести список локализованные компоненты пакета, такие как строки и условий лицензии на использование файла package.xml манифеста.  
  
-   Документ для условия лицензии.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Шаг 1: Чтобы создать каталог начального загрузчика  
  
1.  Создайте каталог с именем **UpdateConsentDialog** в %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Может потребоваться права администратора, чтобы создать эту папку.  
  
2.  В каталоге UpdateConsentDialog создайте подкаталог с именем en.  
  
    > [!NOTE]
    >  Создайте новый каталог для каждого языкового стандарта. Например можно добавить вложенные папки для языковых стандартов fr и de. Эти каталоги могут содержать строки, французском и немецком языках и языковых пакетов, при необходимости.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Шаг 2: Чтобы создать файл манифеста product.xml  
  
1.  Создайте текстовый файл с именем `product.xml`.  
  
2.  В файле product.xml добавьте следующий код XML. Убедитесь, что не перезаписывать существующий XML-код.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Сохраните файл в каталог начального загрузчика UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Шаг 3: Создание манифеста package.xml файла и программное обеспечение лицензионного соглашения  
  
1.  Создайте текстовый файл с именем `package.xml`.  
  
2.  В файле package.xml добавьте следующий код XML для определения языкового стандарта и включают условия лицензии программного обеспечения. Убедитесь, что не перезаписывать существующий XML-код.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Сохраните файл в en подкаталог в каталоге UpdateConsentDialog начального загрузчика.  
  
4.  Создайте документ с именем eula.rtf для условий лицензии на использование.  
  
    > [!NOTE]
    >  Условия лицензионного соглашения программного обеспечения должны включать информацию о лицензировании, никаких гарантий, обязательств и местным законодательством. Эти файлы должны быть языковому стандарту, поэтому убедитесь, что файл сохранен в формате, который поддерживает символы MBCS или UNICODE. Обратитесь в юридический отдел о содержимом условий лицензионного соглашения программного обеспечения.  
  
5.  Сохраните документ в подкаталоге en в каталоге UpdateConsentDialog начального загрузчика.  
  
6.  При необходимости создайте новый файл манифеста package.xml и документа eula.rtf для условий лицензии на использование для каждого языкового стандарта. Например при создании вложенные папки для языковых стандартов fr и de, создаются отдельные файлы манифеста package.xml и условия лицензии и сохраняются в подкаталоги fr и de.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>Установку приложения согласия на обновления в качестве необходимого компонента  
 В Visual Studio можно задать приложение согласия как необходимый компонент.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Для установки приложения согласия на обновления в качестве необходимого компонента  
  
1.  В **обозревателе решений**, щелкните имя приложения, которое требуется развернуть.  
  
2.  На **проекта** меню, нажмите кнопку *ProjectName* **свойства**.  
  
3.  Нажмите кнопку **публикации** и нажмите кнопку **необходимых компонентов**.  
  
4.  Выберите **обновить диалоговое окно согласия**.  
  
    > [!NOTE]
    >  Может потребоваться закрыть и снова открыть Visual Studio для просмотра Update Consent Dialog в диалоговом окне необходимых компонентов.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="creating-and-testing-the-setup-program"></a>Создание и тестирование программы установки  
 После выбора приложение согласия в качестве необходимого компонента можно создать установщик и начального загрузчика для вашего приложения.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Создать и проверить программу установки, не нажав кнопку принимаю  
  
1.  В **обозревателе решений**, щелкните имя приложения, которое требуется развернуть.  
  
2.  На **проекта** меню, нажмите кнопку *ProjectName* **свойства**.  
  
3.  Нажмите кнопку **публикации** и нажмите кнопку **Опубликовать сейчас**.  
  
4.  Если выходные данные публикации не открывается автоматически, перейдите к результату.  
  
5.  Запустите программу Setup.exe.  
  
     Программа установки показывает лицензионное соглашение диалоговом окне согласия обновления программного обеспечения.  
  
6.  Прочтите лицензионное соглашение и нажмите кнопку **Accept**.  
  
     Приложение Update Consent Dialog расположена и содержит следующий текст: приложение, которое вы собираетесь установить проверяет наличие последних обновлений в Интернете. Щелкнув принимаю авторизовать приложение для проверки наличия обновлений автоматически в Интернете.  
  
7.  Закройте приложение, или нажмите кнопку "Отмена".  
  
     Приложение отобразит ошибку: произошла ошибка при установке системных компонентов для *ApplicationName*. Продолжение установки невозможно, пока все системные компоненты успешно установлены.  
  
8.  Нажмите кнопку Подробнее, чтобы отобразить следующее сообщение об ошибке: компонент Update Consent Dialog не удалось установить следующее сообщение об ошибке: «соглашение для автоматического обновления не принимается.» Не удалось установить следующие компоненты:-Update Consent Dialog  
  
9. Нажмите кнопку **Закрыть**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Создать и проверить программу установки, нажав кнопку принимаю  
  
1.  В **обозревателе решений**, щелкните имя приложения, которое требуется развернуть.  
  
2.  На **проекта** меню, нажмите кнопку *ProjectName* **свойства**.  
  
3.  Нажмите кнопку **публикации** и нажмите кнопку **Опубликовать сейчас**.  
  
4.  Если выходные данные публикации не открывается автоматически, перейдите к результату.  
  
5.  Запустите программу Setup.exe.  
  
     Программа установки показывает лицензионное соглашение диалоговом окне согласия обновления программного обеспечения.  
  
6.  Прочтите лицензионное соглашение и нажмите кнопку **Accept**.  
  
     Приложение Update Consent Dialog расположена и содержит следующий текст: приложение, которое вы собираетесь установить проверяет наличие последних обновлений в Интернете. Щелкнув принимаю авторизовать приложение для проверки наличия обновлений автоматически в Интернете.  
  
7.  Нажмите кнопку **принимаю**, а затем нажмите кнопку **Продолжение**.  
  
     Приложение начинает установку.  
  
8.  Если появится диалоговое окно установки приложения, щелкните **установить**.  
  
## <a name="see-also"></a>См. также  
 [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)   
 [Создание пакетов загрузчика](../deployment/creating-bootstrapper-packages.md)   
 [Как: создание манифеста продукта](../deployment/how-to-create-a-product-manifest.md)   
 [Как: создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md)   
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)