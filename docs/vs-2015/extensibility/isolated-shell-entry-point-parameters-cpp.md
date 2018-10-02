---
title: Изолированная параметры точки входа оболочки (C++) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 174deddd0783c53aecd5e2edd361587bbb02cb34
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568466"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Параметры точки входа изолированной оболочки (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [изолированной оболочки запись точки параметров (C++)](https://docs.microsoft.com/visualstudio/extensibility/isolated-shell-entry-point-parameters-cpp).  
  
При запуске приложения на основе оболочки Visual Studio, он вызывает начальную точку входа оболочки Visual Studio. Следующие параметры можно переопределить в вызове начальную точку входа оболочки. Описание каждого параметра, см. в разделе [. Файлов pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   AppName  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 Шаблон изолированную оболочку Visual Studio создает файл с исходным *solutionName*.cpp, где *solutionName* именем решения для приложения. Этот файл определяет главную точку входа для приложения, функция _tWinMain. Эта функция вызывает начальную точку входа оболочки.  
  
 Можно изменить поведение приложения, изменив эти параметры при запуске приложения.  
  
## <a name="parameters"></a>Параметры  
 Точки входа запуска оболочки Visual Studio определяет пять параметров. Не изменяйте первые четыре параметра. Пятый параметр принимает список переопределение параметров. Точки входа запуска оболочки вызывается из главную точку входа приложения.  
  
 Точки входа запуска оболочки имеет следующую сигнатуру.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Если вы не хотите переопределять любые настройки приложения, оставьте значения параметров, переопределяют параметр является пустым указателем.  
  
 Чтобы переопределить один или несколько параметров, передайте строку Юникода, содержащий параметры для переопределения. Строка является разделенный точками с запятой список пар "имя значение". Каждая пара содержит имя параметра для переопределения, следуют знак равенства (=), а затем значение, которое применяется к параметру.  
  
> [!NOTE]
>  Не используйте пробелы в строках Юникода.  
  
 Для логических параметров следующие строки представляют значение true; все другие строки представляют значение false. Эти строки не учитывается регистр.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   вкл.  
  
-   true  
  
-   да  
  
## <a name="example"></a>Пример  
 Чтобы отключить надстройки или изменение расположения проектов по умолчанию для вашего приложения, можно задать последний параметр «AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp».  
  
## <a name="see-also"></a>См. также  
 [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md)   
 [Файлы .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

