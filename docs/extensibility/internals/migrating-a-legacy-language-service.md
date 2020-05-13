---
title: Миграция службы языка наследия (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707110"
---
# <a name="migrating-a-legacy-language-service"></a>Миграция языковой службы прежних версий
Вы можете перенести устаревший языковой сервис на более позднюю версию Visual Studio, обновив проект и добавив файл source.extension.vsixmanifest в проект. Сам языковой сервис будет продолжать функционировать, как и прежде, потому что редактор Visual Studio адаптирует его.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации языковой [службы,](../../extensibility/editor-and-language-service-extensions.md)см.

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Миграция Визуальной студии 2008 Языковое обслуживание решение для более поздней версии
 Следующие шаги показывают, как адаптировать образную студию 2008 образец под названием RegExLanguageService. Вы можете найти этот образец в Visual Studio 2008 SDK установки, в *Visual Studio SDK установки путь*"VisualStudioIntegration"ОбразнаяСтудияИнтеграция "Образцы"IDE-CSharp-Пример.RegExLanguageService папку.

> [!IMPORTANT]
> Если языковая служба не определяет цвета, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> необходимо `true` явно установить на VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Перенести языковую службу Visual Studio 2008 в более позднюю версию

1. Установите новые версии Visual Studio и Visual Studio SDK. Для получения дополнительной информации о способах установки SDK, [см.](../../extensibility/installing-the-visual-studio-sdk.md)

2. Отобразите файл RegExLangServ.csproj (без загрузки в Visual Studio.

     В `Import` узло, отсылаемом к файлу Microsoft.VsSDK.targets, замените значение следующим текстом.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Сохранить файл, а затем закрыть его.

4. Откройте решение RegExLangServ.sln.

5. Отображается окно **обновления в одну сторону.** Нажмите кнопку **ОК**.

6. Обновление свойств проекта. Откройте окно **Project Properties,** выбрав узла проекта в **solution Explorer,** нажав правой кнопкой и выбрав **свойства.**

    - На вкладке **Приложения** измените **платформу Target** до **4.6.1**.

    - На вкладке **Debug,** в поле **внешней программы «Старт»,** введите ** \<путь установки Visual Studio>»Common7-IDE'devenv.exe.**.

         В поле **аргументов командной строки,** тип /**корниuffис Exp**.

7. Обновление следующих ссылок:

    - Удалите ссылку на Microsoft.VisualStudio.Shell.9.0.dll, затем добавьте ссылки на Microsoft.VisualStudio.Shell.14.0.dll и Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Удалить ссылку на Microsoft.VisualStudio.Package.LanguageService.9.0.dll, а затем добавить ссылку на Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Добавить ссылку на Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Откройте файл VsPkg.cs и измените значение атрибута на `DefaultRegistryRoot`

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Первоначальный образец не регистрирует свою языковую службу, поэтому необходимо добавить следующий атрибут в VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Необходимо добавить файл source.extension.vsixmanifest.

    - Копируйте этот файл из существующего расширения в каталог проекта. (Один из способов получить этот файл заключается в создании проекта VSIX (под **файлом,** нажмите **Новый**, затем нажмите **проекта**. В рамках Visual Basic или C' нажмите **Расширительность**, а затем выберите **VSIX проекта**.)

    - Добавьте полученный файл в проект.

    - В **свойствах**файла, установить **действие сборки** **нет**.

    - Откройте файл с **vSIX Manifest редактором**.

    - Измените следующие поля:

    - **ID**: RegExLangServ

    - **Название продукта**: RegExLangServ

    - **Описание**: Регулярная служба языка выражения.

    - Под **активами**, нажмите **Новый**, выберите **тип** **Microsoft.VisualStudio.VsPackage**, установить **источник** проекта в **текущем решении**, а затем установить **проект** **RegExLangServ**.

    - Сохраните файл и закройте его.

11. Создайте решение. Встроенные файлы развернуты в **%USERPROFILE% -AppData-Местный -Microsoft-VisualStudio -14.0Exp-Расширения -MSIT - RegExLangServ\\**.

12. Приступите к отладке. Открылся второй экземпляр Visual Studio.

## <a name="see-also"></a>См. также
- [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)
