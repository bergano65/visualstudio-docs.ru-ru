---
title: Элементы изолированной оболочки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204602"
---
# <a name="elements-of-the-isolated-shell"></a>Элементы изолированной оболочки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете изменить параметры реестра, параметры времени выполнения и точку входа приложения для изолированного приложения оболочки, а также файлы vsct, pkgdef и pkgundef.  
  
## <a name="registry-settings"></a>Параметры реестра  
 Файлы. pkgdef и. pkgundef изменяют параметры реестра для приложения изолированной оболочки. При запуске приложения параметры реестра определяются в следующей последовательности:  
  
 При запуске приложения параметры реестра определяются в следующей последовательности:  
  
1. Создается раздел реестра для приложения.  
  
2. Реестр обновляется из файла pkgdef приложения путем определения указанных ключей и записей.  
  
3. Для каждого пакета, который является частью приложения, реестр обновляется из файла pkgdef этого пакета. Каждый пакет определяется в файле pkgdef приложения с помощью ключа $RootKey $ \Паккажес \\ {*вспаккажегуид*} для пакета.  
  
4. Реестр обновляется из Аппенвконфиг. pkgdef и Басеконфиг. pkgdef в каталоге *установки пакета SDK для Visual Studio*\Common7\IDE\ShellExtensions\Platform. Эти файлы являются частью Visual Studio, а также частью распространяемого пакета Visual Studio Shell (изолированного режима).  
  
5. Реестр обновляется из pkgundef-файла приложения путем удаления указанных ключей и записей.  
  
## <a name="run-time-settings"></a>Параметры времени выполнения  
 Когда пользователь запускает приложение изолированной оболочки, он вызывает начальную точку входа оболочки Visual Studio. Параметры приложения определяются при запуске приложения следующим образом.  
  
1. Оболочка Visual Studio проверяет реестр приложений на наличие конкретных ключей. Если параметр для ключа указан в вызове начальной точки входа, это значение переопределяет значение в реестре.  
  
2. Если ни реестр, ни параметр точки входа не задает значение параметра, используется значение по умолчанию для параметра.  
  
   Когда пользователь запускает приложение из командной строки, все параметры командной строки передаются в оболочку Visual Studio, которая обрабатывает их так же, как и в devenv. Дополнительные сведения о параметрах команды devenv см. в разделе [Параметры командной строки devenv](../ide/reference/devenv-command-line-switches.md) и [Параметры командной строки devenv для разработки VSPackage](../extensibility/devenv-command-line-switches-for-vspackage-development.md). Дополнительные сведения о регистрации пакета для параметров командной строки см. в разделе [Добавление параметров командной строки](../extensibility/adding-command-line-switches.md).  
  
## <a name="the-start-entry-point"></a>Начальная точка входа  
 Файл Appenvstub.dll содержит точки входа для доступа к изолированной оболочке. При запуске приложения вызывается начальная точка входа Appenvstub.dll.  
  
 Поведение приложения можно изменить, изменив значение последнего параметра, который передается в начальную точку входа. Дополнительные сведения см. в разделе [Параметры точки входа изолированной оболочки (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md).  
  
## <a name="the-vsct-file"></a>Тот. Файл vsct  
 Файл. vsct позволяет указать, какие стандартные элементы пользовательского интерфейса Visual Studio доступны в приложении. Дополнительные сведения см. в разделе [. Vsct файлы](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md).  
  
## <a name="the-pkgundef-file"></a>Тот. Файл Pkgundef  
 При установке приложения на компьютер, на котором уже установлена Visual Studio, для приложения вносится копия записей реестра Visual Studio. По умолчанию приложение использует пакеты VSPackage, которые уже установлены на компьютере. Файл. pkgundef позволяет исключить записи реестра для удаления конкретных элементов оболочки или расширений Visual Studio из приложения. Дополнительные сведения см. в разделе [. Pkgundef файлы](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Файл. pkgundef позволяет исключить записи реестра для удаления конкретных элементов оболочки или расширений Visual Studio из приложения. Дополнительные сведения см. в разделе [. Pkgundef файлы](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md).  
  
 Набор идентификаторов GUID пакета, которые можно исключить, указан в списке [идентификаторы GUID пакета компонентов Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
## <a name="the-pkgdef-file"></a>Тот. Файл pkgdef  
 Pkgdef-файл позволяет определить записи реестра для приложения, которые задаются при установке приложения. Описание файла pkgdef и списка записей реестра, используемых оболочкой Visual Studio, см. в разделе [. Файлы pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
## <a name="substitution-strings"></a>Строки подстановки  
 Строки подстановки, используемые в файлах. pkgdef и. pkgundef, перечислены в [строках подстановки, используемых в. Pkgdef и. Pkgundef файлы](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
## <a name="other-settings"></a>Другие параметры  
 Если изолированное приложение оболочки зависит от Microsoft.VisualStudio.GraphModel.dll, необходимо добавить следующее перенаправление привязки в файл. config приложения изолированной оболочки:  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
