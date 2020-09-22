---
title: Миграция языковой службы прежних версий | Документация Майкрософт
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
ms.openlocfilehash: bc6c5d665367f2d5af9e2dd6d2a7d664e50f4830
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843092"
---
# <a name="migrating-a-legacy-language-service"></a>Миграция языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вы можете перенести устаревшую языковую службу в более позднюю версию Visual Studio, обновив проект и добавив файл Source. extension. vsixmanifest в проект. Сама языковая служба будет работать, как и раньше, поскольку редактор Visual Studio адаптирует его.  
  
 Устаревшие языковые службы реализуются как часть VSPackage, но более новым способом реализации функций языковой службы является использование расширений MEF. Дополнительные сведения о новом способе реализации языковой службы см. в статье [расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Рекомендуется как можно скорее начать использовать новый API редактора. Это улучшит производительность языковой службы и позволит использовать новые функции редактора.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Миграция решения Visual Studio 2008 Language Service в более позднюю версию  
 Ниже описано, как адаптировать пример Visual Studio 2008 с именем Режекслангуажесервице. Этот пример можно найти в установке пакета SDK для Visual Studio 2008 в папке *путь установки пакета SDK для Visual Studio*\висуалстудиоинтегратион\самплес\иде\кшарп\ексампле.режекслангуажесервице\.  
  
> [!IMPORTANT]
> Если языковая служба не определяет цвета, необходимо явно задать для пакета <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Миграция языковой службы Visual Studio 2008 в более позднюю версию  
  
1. Установите более новые версии Visual Studio и Visual Studio SDK. Дополнительные сведения о способах установки пакета SDK см. [в разделе Установка пакета SDK для Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2. Измените файл Режекслангсерв. csproj (не загружая его в Visual Studio).  
  
     В `Import` узле, который ссылается на файл Microsoft. VsSDK. targets, замените значение следующим текстом.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3. Сохраните файл и закройте его.  
  
4. Откройте решение Режекслангсерв. sln.  
  
5. Откроется окно **одностороннего обновления** . Нажмите кнопку **ОК**.  
  
6. Обновите свойства проекта. Откройте окно **свойств проекта** , выбрав узел проекта в **Обозреватель решений**, щелкните правой кнопкой мыши и выберите пункт **Свойства**.  
  
    - На вкладке **приложение** измените **целевую платформу** на **4.6.1**.  
  
    - На вкладке **Отладка** в поле **Запуск внешней программы** введите ** \<Visual Studio installation path>\Common7\IDE\devenv.exe.**.  
  
         В поле **аргументы командной строки** введите/**рутсуффикс exp**.  
  
7. Обновите следующие ссылки:  
  
    - Удалите ссылку на Microsoft.VisualStudio.Shell.9.0.dll, а затем добавьте ссылки на Microsoft.VisualStudio.Shell.14.0.dll и Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    - Удалите ссылку на Microsoft.VisualStudio.Package.LanguageService.9.0.dll, а затем добавьте ссылку на Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    - Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8. Откройте файл VsPkg.cs и измените значение `DefaultRegistryRoot` атрибута на  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. В исходном примере не регистрируется языковая служба, поэтому необходимо добавить следующий атрибут в VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Необходимо добавить файл Source. extension. vsixmanifest.  
  
    - Скопируйте этот файл из существующего расширения в каталог проекта. (Один из способов получить этот файл — создать проект VSIX (в разделе **файл**выберите **создать**, а затем — **проект**). В разделе Visual Basic или C# щелкните **расширяемость**, а затем выберите **проект VSIX**.)  
  
    - Добавьте полученный файл в проект.  
  
    - В **свойствах**файла задайте для параметра **действие сборки** значение **нет**.  
  
    - Откройте файл с помощью **редактора манифеста VSIX**.  
  
    - Измените следующие поля:  
  
    - **Идентификатор**: режекслангсерв  
  
    - **Имя продукта**: режекслангсерв  
  
    - **Описание**: служба языка регулярных выражений.  
  
    - В **разделе активы**щелкните **создать**, выберите **Тип** в **Microsoft. VisualStudio. VSPackage**, задайте в качестве **источника** **проект в текущем решении**, а затем задайте для **проекта** значение **режекслангсерв**.  
  
    - Сохраните и закройте файл.  
  
11. Создайте решение. Созданные файлы развертываются в **%UserProfile%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ режекслангсерв \\ **.  
  
12. Запустите отладку. Второй экземпляр Visual Studio открыт.  
  
## <a name="see-also"></a>См. также:  
 [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)
