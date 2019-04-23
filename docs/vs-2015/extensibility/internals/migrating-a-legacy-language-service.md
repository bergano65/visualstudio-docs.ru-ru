---
title: Миграция языковой службы прежних | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe6870046d1dd15c7bc5795dd82d393272ca6b1e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097366"
---
# <a name="migrating-a-legacy-language-service"></a>Миграция языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Можно перенести языковой службы прежних версий до более поздней версии Visual Studio путем обновления проекта и добавление в проект файл source.extension.vsixmanifest. Сама служба языка будет продолжать работать по-прежнему, так как в редакторе Visual Studio адаптирует его.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы подробнее узнать о новых способах реализации языковой службы, см. в разделе [редактора и языковой службы расширения](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Переход на более поздней версии Visual Studio 2008 решения на языке службы  
 Ниже показано, как адаптировать с именем RegExLanguageService пример Visual Studio 2008. В этом примере в установке Visual Studio 2008 SDK можно найти в *путь установки Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ папки.  
  
> [!IMPORTANT]
>  Если служба языка не определять цвета, необходимо явно задать <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> для `true` в VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Для переноса языковой службы Visual Studio 2008 до более поздней версии  
  
1. Установка более новых версиях Visual Studio и Visual Studio SDK. Дополнительные сведения о способах установки пакета SDK см. в разделе [установка Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2. Измените файл RegExLangServ.csproj (без загрузки его в Visual Studio.  
  
     В `Import` узел, который ссылается на файл Microsoft.VsSDK.targets, замените значение со следующим текстом.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3. Сохраните файл и закройте его.  
  
4. Откройте решение RegExLangServ.sln.  
  
5. **Одностороннее обновление** появится окно. Нажмите кнопку **ОК**.  
  
6. Обновление свойств проекта. Откройте **свойства проекта** окно, выбрав узел проекта в **обозревателе решений**, щелкните правой кнопкой мыши и выбрав **свойства**.  
  
    - На **приложения** вкладке **требуемой версии .NET framework** для **4.6.1**.  
  
    - На **Отладка** на вкладке **запуск внешней программы** введите  **\<путь установки Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         В **аргументы командной строки** введите /**rootsuffix Exp**.  
  
7. Обновите следующие ссылки:  
  
    - Удалите ссылку на Microsoft.VisualStudio.Shell.9.0.dll, а затем добавьте ссылки на Microsoft.VisualStudio.Shell.14.0.dll и Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    - Удалите ссылку на Microsoft.VisualStudio.Package.LanguageService.9.0.dll, а затем добавьте ссылку на Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    - Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8. Откройте файл VsPkg.cs и измените значение свойства `DefaultRegistryRoot` для атрибута  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. Исходный образец не регистрирует его языковой службы, которую необходимо добавить следующий атрибут VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. You must add a source.extension.vsixmanifest file.  
  
    - Скопируйте этот файл из существующего расширения в каталог проекта. (Лучший способ получить этот файл является создание проекта VSIX (в разделе **файл**, нажмите кнопку **New**, затем нажмите кнопку **проекта**. В Visual Basic или C#, выберите **расширяемости**, а затем выберите **проект VSIX**.)  
  
    - Добавьте файл в проект.  
  
    - В файле **свойства**, задайте **действие при построении** для **None**.  
  
    - Откройте файл с **Редактор манифестов VSIX**.  
  
    - Измените следующие поля:  
  
    - **ИДЕНТИФИКАТОР**: RegExLangServ  
  
    - **Название продукта**: RegExLangServ  
  
    - **Описание**. Служба языка регулярных выражений.  
  
    - В разделе **активы**, нажмите кнопку **New**выберите **тип** для **Microsoft.VisualStudio.VsPackage**, задайте **источника** для **проект в текущем решении**, а затем задайте **проекта** для **RegExLangServ**.  
  
    - Сохраните и закройте файл.  
  
11. Постройте решение. Созданные файлы развертываются **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Приступите к отладке. Открыть второй экземпляр Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)
