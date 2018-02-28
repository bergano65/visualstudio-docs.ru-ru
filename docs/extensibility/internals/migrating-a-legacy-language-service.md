---
title: "Миграция языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4f5f7cff29dd368acbbc3f599ec0cf623343031f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-a-legacy-language-service"></a>Миграция языковую службу прежних версий
Можно перенести устаревших языковую службу до более поздней версии Visual Studio путем обновления проекта и добавление в проект файл source.extension.vsixmanifest. Языковая служба сама будет продолжать работать как и прежде, так как в редакторе Visual Studio использует ее.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Чтобы больше узнать о новых способ реализации языковую службу, в разделе [редактора и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Миграция решение службы языка Visual Studio 2008 в более поздней версии  
 Ниже показано, как адаптировать с именем RegExLanguageService образец Visual Studio 2008. В этом примере при установке SDK для Visual Studio 2008 можно найти в *путь установки Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ папки.  
  
> [!IMPORTANT]
>  Если службе языка не определяет цвета, необходимо явно задать <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> для `true` в VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Чтобы перенести языковую службу Visual Studio 2008 до более поздней версии  
  
1.  Установка новой версии Visual Studio и пакет SDK для Visual Studio. Дополнительные сведения о способах установки пакета SDK см. в разделе [Установка пакета SDK для Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Измените файл RegExLangServ.csproj (без, загрузив его в Visual Studio.  
  
     В `Import` узел, который ссылается на файл Microsoft.VsSDK.targets, замените значение со следующим текстом.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Сохраните файл и закройте его.  
  
4.  Откройте решение RegExLangServ.sln.  
  
5.  **Одностороннее обновление** появится окно. Нажмите кнопку **ОК**.  
  
6.  Обновите свойства проекта. Откройте **свойства проекта** , выбрав узел проекта в **обозревателе решений**, щелкните правой кнопкой мыши и выбрав **свойства**.  
  
    -   На **приложения** измените **требуемой версии .NET framework** для **4.6.1**.  
  
    -   На **отладки** вкладке **запуск внешней программы** введите  **\<путь установки Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         В **аргументы командной строки** введите /**rootsuffix Exp**.  
  
7.  Обновите следующие ссылки:  
  
    -   Удалите ссылку на Microsoft.VisualStudio.Shell.9.0.dll, а затем добавьте ссылки на Microsoft.VisualStudio.Shell.14.0.dll и Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Удалите ссылку на Microsoft.VisualStudio.Package.LanguageService.9.0.dll, а затем добавьте ссылку на Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Откройте файл VsPkg.cs и измените значение `DefaultRegistryRoot` для атрибута  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Исходный образец не регистрирует его языковой службы, которую необходимо добавить следующий атрибут VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Необходимо добавить файл source.extension.vsixmanifest.  
  
    -   Скопируйте этот файл из существующего модуля в каталог проекта. (Единственный способ получить этот файл является создание проекта VSIX (под **файл**, нажмите кнопку **New**, нажмите кнопку **проекта**. В Visual Basic или C#, выберите **расширяемости**, а затем выберите **проект VSIX**.)  
  
    -   Добавьте файл в проект.  
  
    -   В файле **свойства**, задайте **действие при построении** для **нет**.  
  
    -   Откройте файл с **редактора манифеста VSIX**.  
  
    -   Измените следующие поля:  
  
    -   **Идентификатор**: RegExLangServ  
  
    -   **Название продукта**: RegExLangServ  
  
    -   **Описание**: языковую службу регулярного выражения.  
  
    -   В разделе **активы**, нажмите кнопку **New**выберите **тип** для **Microsoft.VisualStudio.VsPackage**, задайте **источника** для **проект в текущем решении**, а затем задайте **проекта** для **RegExLangServ**.  
  
    -   Сохраните и закройте файл.  
  
11. Постройте решение. Файлы построения развертываются **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Приступите к отладке. Открыть второй экземпляр Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)