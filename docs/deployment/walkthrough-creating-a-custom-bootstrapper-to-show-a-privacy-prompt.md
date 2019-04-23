---
title: Пошаговое руководство. Создание пользовательского загрузчика с предупреждением о конфиденциальности | Документация Майкрософт
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1973d5d71308cc5fda6e48acfc60d256775ff2cc
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089176"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Пошаговое руководство. Создание пользовательского загрузчика с предупреждением о конфиденциальности
Можно настроить приложений ClickOnce для автоматического обновления при появлении сборок с более новые версии файла и версии сборки. Чтобы убедиться в том, что пользователи согласны такое поведение, можно отобразить предупреждением о конфиденциальности на них. После этого можно разрешить приложению для автоматического обновления. Если приложение не может быть автоматическое обновление, он не устанавливаются.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- Visual Studio 2010.

## <a name="create-an-update-consent-dialog-box"></a>Создайте в диалоговом окне согласия
 Чтобы отобразить предупреждением о конфиденциальности, создайте приложение, запрашивающее у пользователя согласие на автоматическое обновление для приложения.

#### <a name="to-create-a-consent-dialog-box"></a>Для создания диалогового окна подтверждения

1. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

2. В **новый проект** диалоговом окне щелкните **Windows**, а затем нажмите кнопку **WindowsFormsApplication**.

3. Для **имя**, тип **ConsentDialog**, а затем нажмите кнопку **ОК**.

4. В конструкторе щелкните форму.

5. В **свойства** измените **текст** свойства **диалоговое окно согласия обновления**.

6. В **элементов**, разверните **все формы Windows Forms**и перетащите **метка** на форму элемент управления.

7. В конструкторе щелкните элемент управления label.

8. В **свойства** измените **текст** свойства в разделе **внешний вид** следующим:

    Приложение, которое вы собираетесь установить проверяет наличие последних обновлений в Интернете. Нажимая кнопку «Принимаю», вы разрешаете приложению искать и устанавливать обновления автоматически из Интернета.

9. В **элементов**, перетащите **флажок** элемента управления в середину формы.

10. В **свойства** измените **текст** свойства в разделе **макета** для **принимаю**.

11. В **элементов**, перетащите **кнопку** элемента управления в левом нижнем углу формы.

12. В **свойства** измените **текст** свойства в разделе **макета** для **Продолжить**.

13. В **свойства** измените **(имя)** свойства в разделе **разработки** для **значение ProceedButton**.

14. В **элементов**, перетащите **кнопку** элемента управления в правом нижнем углу формы.

15. В **свойства** измените **текст** свойства в разделе **макета** для **отменить**.

16. В **свойства** измените **(имя)** свойства в разделе **разработки** для **CancelButton**.

17. В конструкторе, дважды щелкните **принимаю** флажок, чтобы создать обработчик события CheckedChanged.

18. В файле кода Form1 добавьте следующий код в обработчик события CheckedChanged.

     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]

19. Измените конструктор класса, чтобы отключить **Продолжить** кнопку по умолчанию.

     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]

20. В файле кода Form1 добавьте следующий код для логическая переменная для отслеживания, если конечный пользователь предоставил обновлений в Интернете.

     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]

21. В конструкторе, дважды щелкните **Продолжить** кнопку, чтобы создать обработчик событий Click.

22. В файле кода Form1 добавьте следующий код в обработчик событий Click для **Продолжить** кнопки.

     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]

23. В конструкторе, дважды щелкните **отменить** кнопку, чтобы создать обработчик событий Click.

24. В файле кода Form1 добавьте следующий код в обработчик событий Click для **отменить** кнопки.

     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]

25. Обновите приложение, будут возвращать ошибку, если конечный пользователь не дал согласия обновлений в Интернете.

     Для только для разработчиков Visual Basic:

    1. В **обозревателе решений**, нажмите кнопку **ConsentDialog**.

    2. На **проекта** меню, щелкните **добавить модуль**, а затем нажмите кнопку **добавить**.

    3. В *Module1.vb* файл кода, добавьте следующий код.

        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]

    4. На **проекта** меню, нажмите кнопку **Свойства ConsentDialog**, а затем нажмите кнопку **приложения** вкладку.

    5. Снимите флажок **Включить исполняющую**.

    6. В **автоматически запускаемый объект** раскрывающееся меню, выберите **Module1**.

       > [!NOTE]
       >  При отключении платформы приложений отключаются функции, такие как визуальные стили Windows XP, события приложений, экран-заставка, один экземпляр приложения и многое другое. Дополнительные сведения см. в разделе [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

       Visual C# только для разработчиков:

       Откройте *Program.cs* файл кода и добавьте следующий код.

       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]

26. На **построения** меню, щелкните **BuildSolution**.

## <a name="create-the-custom-bootstrapper-package"></a>Создайте пользовательский пакет начального загрузчика
 Чтобы отобразить предупреждением о конфиденциальности для конечных пользователей, можно создать пользовательский пакет начального загрузчика для приложения Update Consent Dialog и включить его в качестве необходимого компонента во всех приложений ClickOnce.

 Ниже описана процедура создания настраиваемого пакета загрузчика, создав в следующих документах:

- Объект *product.xml* файл манифеста, в котором описывается содержимое загрузчика.

- Объект *package.xml* файл манифеста локализованные компоненты пакета, такие как строки и условиями лицензии на программное обеспечение.

- Документ для условия лицензии.

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Шаг 1. Чтобы создать каталог начального загрузчика

1. Создайте каталог с именем **UpdateConsentDialog** в *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*.

    > [!NOTE]
    >  Может потребоваться права администратора, чтобы создать эту папку.

2. В *UpdateConsentDialog* directory, создайте подкаталог с именем *en*.

    > [!NOTE]
    >  Создайте новый каталог для каждого языкового стандарта. Например можно добавить вложенные папки для языковые стандарты fr и de. Эти каталоги могут содержать строки на французском и немецком языках и языковых пакетов, при необходимости.

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Шаг 2. Чтобы создать файл манифеста product.xml

1. Создайте текстовый файл с именем *product.xml*.

2. В *product.xml* добавьте следующий код XML. Убедитесь, что вы не перезаписывать существующий XML-код.

    ```xml
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

3. Сохраните файл в каталог начального загрузчика UpdateConsentDialog.

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Шаг 3. Чтобы создать файл манифеста package.xml и условия лицензии

1. Создайте текстовый файл с именем *package.xml*.

2. В *package.xml* добавьте следующий код XML для определения языкового стандарта и включают условия лицензии. Убедитесь, что вы не перезаписывать существующий XML-код.

    ```xml
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

3. Сохраните файл в en подкаталог в каталоге UpdateConsentDialog начального загрузчика.

4. Создайте документ с именем *eula.rtf* для условия лицензии.

    > [!NOTE]
    >  Условия лицензионного соглашения программного обеспечения должен содержать сведения о лицензировании, никаких гарантий, обязательств и местным законодательством. Эти файлы должны быть зависящих от языкового стандарта, поэтому убедитесь, что файл сохраняется в формате, который поддерживает символы MBCS или Юникод. Проконсультируйтесь с юридическим отделом о содержимом условий лицензионного соглашения на использование программного обеспечения.

5. Сохраните документ в подкаталоге en *UpdateConsentDialog* каталог начального загрузчика.

6. При необходимости создайте новый *package.xml* файла и нового манифеста *eula.rtf* документ для условия лицензии для каждого языкового стандарта. К примеру Если вы создали подкаталоги для языковые стандарты fr и de, создать отдельные файлы манифеста package.xml и условия лицензии и сохранять их в подкаталоги fr и de.

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Приложения согласия на обновления в качестве необходимого компонента
 В Visual Studio можно задать приложение согласия как необходимый компонент.

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Для приложения согласия на обновления в качестве необходимого компонента

1. В **обозревателе решений**, щелкните имя приложения, которое вы хотите развернуть.

2. В меню **Проект** выберите пункт *Имя проекта* **Свойства**.

3. Нажмите кнопку **публикации** странице, а затем выберите **предварительные требования**.

4. Выберите **обновить диалоговое окно согласия**.

    > [!NOTE]
    >  Может потребоваться закрыть и снова открыть Visual Studio для просмотра согласие диалоговое окно обновления в диалоговом окне необходимых компонентов.

5. Нажмите кнопку **ОК**.

## <a name="create-and-test-the-setup-program"></a>Создание и тестирование программы установки
 После настройки приложение согласия в качестве необходимого компонента, можно создать установщик и начального загрузчика для вашего приложения.

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Чтобы создать и протестировать программу установки, не нажав кнопку я принимаю

1. В **обозревателе решений**, щелкните имя приложения, которое вы хотите развернуть.

2. В меню **Проект** выберите пункт *Имя проекта* **Свойства**.

3. Нажмите кнопку **публикации** странице, а затем выберите **Опубликовать сейчас**.

4. Если выходные данные публикации не открывается автоматически, перейдите на выходных данных публикации.

5. Запустите *Setup.exe* программы.

     Программа установки показано диалоговое окно согласия обновления программного обеспечения лицензионного соглашения.

6. Прочтите лицензионное соглашение и нажмите кнопку **Accept**.

     Диалоговое окно согласия обновления приложения отобразится следующий текст: Приложение, которое вы собираетесь установить проверяет наличие последних обновлений в Интернете. Щелкнув я принимаю, вы разрешаете приложению проверять наличие обновлений автоматически в Интернете.

7. Закройте приложение, или нажмите кнопку "Отмена".

     Приложение отображает ошибку: Произошла ошибка при установке системных компонентов для *ApplicationName*. Продолжение установки невозможно, пока не будут успешно установлены все компоненты системы.

8. Нажмите кнопку Подробнее, чтобы отобразить следующее сообщение об ошибке: Диалоговое окно согласия обновления компонента не удалось установить с помощью следующее сообщение об ошибке: «Автоматическое обновление соглашения не принимается.» Не удалось установить следующие компоненты:-диалоговое окно согласия обновления

9. Нажмите кнопку **Закрыть**.

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Чтобы создать и протестировать программу установки, нажав кнопку я принимаю

1. В **обозревателе решений**, щелкните имя приложения, которое вы хотите развернуть.

2. В меню **Проект** выберите пункт *Имя проекта* **Свойства**.

3. Нажмите кнопку **публикации** странице, а затем выберите **Опубликовать сейчас**.

4. Если выходные данные публикации не открывается автоматически, перейдите на выходных данных публикации.

5. Запустите *Setup.exe* программы.

     Программа установки показано диалоговое окно согласия обновления программного обеспечения лицензионного соглашения.

6. Прочтите лицензионное соглашение и нажмите кнопку **Accept**.

     Диалоговое окно согласия обновления приложения отобразится следующий текст: Приложение, которое вы собираетесь установить проверяет наличие последних обновлений в Интернете. Щелкнув я принимаю, вы разрешаете приложению проверять наличие обновлений автоматически в Интернете.

7. Нажмите кнопку **принимаю**, а затем нажмите кнопку **Продолжить**.

     Приложение начинает установку.

8. Если будет открыто диалоговое окно установки приложения, нажмите кнопку **установить**.

## <a name="see-also"></a>См. также
- [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)
- [Создание пакетов начального загрузчика](../deployment/creating-bootstrapper-packages.md)
- [Практическое руководство. Создание манифеста продукта](../deployment/how-to-create-a-product-manifest.md)
- [Практическое руководство. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md)
- [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)