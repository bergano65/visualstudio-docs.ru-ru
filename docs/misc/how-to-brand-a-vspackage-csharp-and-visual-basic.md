---
title: "Практическое руководство. Добавление фирменной символики в пакет VSPackage (C# и Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "диалоговое окно "О программе""
  - "пакеты VSPackage, экраны-заставки"
  - "пакеты VSPackage, фирменная символика"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Практическое руководство. Добавление фирменной символики в пакет VSPackage (C# и Visual Basic)
Появляться в **О программе** диалоговое окно и экран\-заставку, VSPackages, должны реализовывать  <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> интерфейс.  Это обеспечивает следующие сведения [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Имя  
  
-   Идентификатор, как серия или номер версии  
  
-   Сведения  
  
-   Значок эмблемы  
  
 В следующем коде из [Примеры VSSDK](../misc/vssdk-samples.md).  
  
### Реализовать интерфейс IVsInstalledProduct  
  
1.  Добавление <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> атрибут к классу, реализующему VSPackage.  Этот класс должен наследоваться от обоих <xref:Microsoft.VisualStudio.Shell.Package> и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     Первый аргумент, <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>"  <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> атрибут сообщает  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] использование  <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> получить сведения о продукте, вместо этого раздела реестра InstalledProducts.  Остальные аргументы выберите строковые ресурсы для отображения имени продукта, подробностей и идентификатор соответственно.  Однако поскольку первый аргумент `true`, оставшиеся аргументы  `null`.  
  
2.  Щелкните правой кнопкой мыши <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>выберите  **Реализовать интерфейс**, а затем нажмите кнопку  **Реализовать интерфейс**.  
  
3.  Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> с помощью следующего кода.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] вызывает эти методы для получения сведений для затаврить VSPackage.  Метод GetResourceString используется, чтобы локализовать эти сведения.  
  
    > [!NOTE]
    >  Комментарии к коду удалены для краткости.  Можно искать их in [Примеры VSSDK](../misc/vssdk-samples.md).  
  
### Поддержка строки информации о продукте  
  
1.  Дважды щелкните файл ресурсов .resx, связанный с VSPackage.  
  
     Открытие редактора ресурсов.  
  
2.  Найдите и добавьте название продукта, сведения, и идентификатор.  
  
     Следующие строки из ресурса [Примеры VSSDK](../misc/vssdk-samples.md).  
  
     @101  
     Экран\-заставка и Справка пакета о официальном имен \(c\#\).  
  
     @102  
     Этот пакет показано, как отобразить текст и изображение в экран\-заставке и справке о программе.  
  
     @104  
     8.0  
  
3.  Выберите правка и эти сведения.  
  
### Создавать значки и растровые изображения продукта  
  
1.  Добавление растровых изображений и значки в проект как ресурсы проекта.  
  
     Дополнительные сведения см. в разделе [NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/ru-ru/95f15d03-bed0-410c-8d1f-dece5199ba1e).  
  
2.  Закройте редактор ресурсов и снова откройте файл .resx в формате XML или текстовом редакторе.  
  
    > [!NOTE]
    >  Редактор ресурсов не поддерживает присвоить идентификаторы ресурсов к элементам за исключением строк.  
  
3.  Найдите и добавьте ресурсы значков и растрового изображения к файлу .resx.  Следующие ресурсы [Примеры VSSDK](../misc/vssdk-samples.md).  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### Тестирование диалоговое окно о программе и экран\-заставки  
  
-   Для тестирования VSPackage см. в разделе [Практическое руководство. Тестирование окна справки о продукте и экранов\-заставок](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## См. также  
 [Фирменная символика в пакетах VSPackage](/visual-cpp/misc/vspackage-branding)