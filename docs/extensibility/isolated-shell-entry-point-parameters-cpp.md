---
redirect_url: shell/isolated-shell-entry-point-parameters-cpp
title: "Изолированные параметров точки входа оболочки (C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b145207a2c74d47208df391c319f496467ae6438
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Параметров точки входа изолированной оболочки (C++)
При запуске приложения на основе оболочки Visual Studio, он вызывает начальную точку входа оболочки Visual Studio. Следующие параметры могут переопределяться в вызове начальную точку входа оболочки. Описание каждого параметра см. в разделе [. Файлах pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
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
  
 Шаблон изолированной оболочки Visual Studio создает файл исходного *имя_решения*.cpp, где *имя_решения* имя решения для приложения. Этот файл определяет Главная точка входа для приложения, функцией _tWinMain. Эта функция вызывает начальную точку входа оболочки.  
  
 Можно изменить поведение приложения, изменив эти параметры при запуске приложения.  
  
## <a name="parameters"></a>Параметры  
 Точки входа запуска оболочки Visual Studio определяет пять параметров. Не изменяйте первые четыре параметра. Пятый параметр принимает список переопределение параметров. Точки входа запуска оболочки вызывается из главную точку входа приложения.  
  
 Точки входа запуска оболочки имеет следующую сигнатуру.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Если вы не хотите переопределять любые настройки приложения, оставьте значение параметра переопределяет параметр как указатель null.  
  
 Чтобы переопределить один или несколько параметров, передайте строку Юникода, содержащий параметры для переопределения. Строка является список разделенных точкой с запятой пар имя значение. Каждая пара содержит имя параметра, чтобы переопределить, следуют знак равенства (=), а затем значение, которое применяется к параметру.  
  
> [!NOTE]
>  Не включайте пробел в строки в Юникоде.  
  
 Для логических параметров следующие строки представляют значение true; все остальные строки представляют значение false. Эти строки не учитывается.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   вкл.  
  
-   true  
  
-   да  
  
## <a name="example"></a>Пример  
 Чтобы отключить надстройки и изменение расположения проектов по умолчанию для приложения, можно задать последний параметр «AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp».  
  
## <a name="see-also"></a>См. также  
 [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md)   
 [. Файлах pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)