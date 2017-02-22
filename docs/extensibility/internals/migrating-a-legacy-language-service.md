---
title: "Миграция языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы, миграция"
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Миграция языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Путем обновления проекта и добавление в проект файл source.extension.vsixmanifest можно перенести устаревших языковую службу до более поздней версии Visual Studio. Саму службу языка будет продолжать работать как и раньше, поскольку редактор Visual Studio адаптирует его.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Чтобы больше узнать о новый способ реализации службы языка, в разделе [Редактор и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## Перенос решение службы языка Visual Studio 2008 в более поздней версии  
 Ниже показано, как адаптировать пример Visual Studio 2008 с именем RegExLanguageService. В этом примере при установке Visual Studio 2008 SDK можно найти в *путь установки Visual Studio SDK*\\VisualStudioIntegration\\Samples\\IDE\\CSharp\\Example.RegExLanguageService\\ папки.  
  
> [!IMPORTANT]
>  Если служба языка не определить цвета, необходимо явно задать <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> в `true` на VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### Перенос службы языка Visual Studio 2008 для более поздней версии  
  
1.  Установка более новых версий Visual Studio и Visual Studio SDK. Дополнительные сведения о способах установки пакета SDK см. в разделе [Установка Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Измените файл RegExLangServ.csproj \(без загрузки его в Visual Studio.  
  
     В `Import` узел, который ссылается на файл Microsoft.VsSDK.targets, замените значение следующий текст.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Сохраните файл и закройте его.  
  
4.  Откройте решение RegExLangServ.sln.  
  
5.  **Одностороннее обновление** появится окно. Нажмите кнопку **ОК**.  
  
6.  Обновление свойств проекта. Откройте **Свойства проекта** окно, выбрав узел проекта в **обозревателе решений**, щелкните правой кнопкой мыши и выбрав **Свойства**.  
  
    -   На **приложения** измените **Требуемая версия .NET framework** для **4.6.1**.  
  
    -   На **отладки** вкладке **Запуск внешней программы** введите **\\Common7\\IDE\\devenv.exe \< путь установки Visual Studio \>.**.  
  
         В **аргументы командной строки** введите \/**rootsuffix Exp**.  
  
7.  Обновите следующие ссылки:  
  
    -   Удалите ссылку на Microsoft.VisualStudio.Shell.9.0.dll, а затем добавьте ссылки на Microsoft.VisualStudio.Shell.14.0.dll и Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Удалите ссылку на Microsoft.VisualStudio.Package.LanguageService.9.0.dll, а затем добавьте ссылку на Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Откройте файл VsPkg.cs и измените значение `DefaultRegistryRoot` атрибут  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Исходный образец не регистрирует его языковую службу, которую необходимо добавить следующий атрибут VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Необходимо добавить файл source.extension.vsixmanifest.  
  
    -   Скопируйте этот файл из существующего расширения в каталог проекта. \(Один из способов получения файла является создание проекта VSIX \(под **файл**, нажмите кнопку **New**, нажмите кнопку **проекта**. В Visual Basic или C\#, выберите **расширения**, а затем выберите **проект VSIX**.\)  
  
    -   Добавьте файл в проект.  
  
    -   В файле **Свойства**, задайте **Действие при построении** для **Нет**.  
  
    -   Откройте файл с **Редактор манифестов VSIX**.  
  
    -   Измените следующие поля:  
  
    -   **Идентификатор**: RegExLangServ  
  
    -   **Марка**: RegExLangServ  
  
    -   **Описание**: служба языка регулярных выражений.  
  
    -   В разделе **активы**, нажмите кнопку **New**, выберите **тип** для **Microsoft.VisualStudio.VsPackage**, задайте **источника** для **проект в текущем решении**, и задайте **проекта** для **RegExLangServ**.  
  
    -   Сохраните и закройте файл.  
  
11. Постройте решение. Созданные файлы развертываются **%USERPROFILE%\\AppData\\Local\\Microsoft\\VisualStudio\\14.0Exp\\Extensions\\MSIT\\ RegExLangServ\\**.  
  
12. Приступите к отладке. Открыть второй экземпляр Visual Studio.  
  
## См. также  
 [Расширяемость устаревших языковой службы](../../extensibility/internals/legacy-language-service-extensibility.md)