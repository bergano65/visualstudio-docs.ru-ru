---
title: Миграция языковой службы прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1027d4b834f1ffdd2289ced2ee5523c20f9d2353
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726697"
---
# <a name="migrating-a-legacy-language-service"></a>Миграция языковой службы прежних версий
Вы можете перенести устаревшую языковую службу в более позднюю версию Visual Studio, обновив проект и добавив файл Source. extension. vsixmanifest в проект. Сама языковая служба будет работать, как и раньше, поскольку редактор Visual Studio адаптирует его.

 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации языковой службы см. в статье [расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Миграция решения Visual Studio 2008 Language Service в более позднюю версию
 Ниже описано, как адаптировать пример Visual Studio 2008 с именем Режекслангуажесервице. Этот пример можно найти в установке пакета SDK для Visual Studio 2008 в папке *путь установки пакета SDK для Visual Studio*\висуалстудиоинтегратион\самплес\иде\кшарп\ексампле.режекслангуажесервице\.

> [!IMPORTANT]
> Если языковая служба не определяет цвета, необходимо явно задать <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> для `true` в VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Миграция языковой службы Visual Studio 2008 в более позднюю версию

1. Установите более новые версии Visual Studio и Visual Studio SDK. Дополнительные сведения о способах установки пакета SDK см. [в разделе Установка пакета SDK для Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).

2. Измените файл Режекслангсерв. csproj (не загружая его в Visual Studio).

     В узле `Import`, который ссылается на файл Microsoft. VsSDK. targets, замените значение на приведенный ниже текст.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Сохраните файл и закройте его.

4. Откройте решение Режекслангсерв. sln.

5. Откроется окно **одностороннего обновления** . Нажмите кнопку **ОК**.

6. Обновите свойства проекта. Откройте окно **свойств проекта** , выбрав узел проекта в **Обозреватель решений**, щелкните правой кнопкой мыши и выберите пункт **Свойства**.

    - На вкладке **приложение** измените **целевую платформу** на **4.6.1**.

    - На вкладке **Отладка** в поле **Запуск внешней программы** введите **путь установки \<Visual Studio > \Common7\IDE\devenv.exe.** .

         В поле **аргументы командной строки** введите/**рутсуффикс exp**.

7. Обновите следующие ссылки:

    - Удалите ссылку на Microsoft. VisualStudio. Shell. 9.0. dll, а затем добавьте ссылки на Microsoft. VisualStudio. Shell. г. dll и Microsoft. VisualStudio. Shell. unmutable. 11.0. dll.

    - Удалите ссылку на Microsoft. VisualStudio. Package. Лангуажесервице. 9.0. dll, а затем добавьте ссылку на Microsoft. VisualStudio. Package. Лангуажесервице. г. dll.

    - Добавьте ссылку на Microsoft. VisualStudio. Shell. Interop. 10.0. dll.

8. Откройте файл VsPkg.cs и измените значение атрибута `DefaultRegistryRoot` на

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. В исходном примере не регистрируется языковая служба, поэтому необходимо добавить следующий атрибут в VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Необходимо добавить файл Source. extension. vsixmanifest.

    - Скопируйте этот файл из существующего расширения в каталог проекта. (Один из способов получить этот файл — создать проект VSIX (в разделе **файл**выберите **создать**, а затем — **проект**). В разделе Visual Basic C# или щелкните **расширяемость**, а затем выберите **проект VSIX**.)

    - Добавьте файл в проект.

    - В **свойствах**файла задайте для параметра **действие сборки** значение **нет**.

    - Откройте файл с помощью **редактора манифеста VSIX**.

    - Измените следующие поля:

    - **Идентификатор**: режекслангсерв

    - **Имя продукта**: режекслангсерв

    - **Описание**: служба языка регулярных выражений.

    - В **разделе активы**щелкните **создать**, выберите **Тип** в **Microsoft. VisualStudio. VSPackage**, задайте в качестве **источника** **проект в текущем решении**, а затем задайте для **проекта** значение **режекслангсерв**.

    - Сохраните и закройте файл.

11. Постройте решение. Созданные файлы развертываются в **%UserProfile%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ режекслангсерв \\** .

12. Приступите к отладке. Второй экземпляр Visual Studio открыт.

## <a name="see-also"></a>См. также
- [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)