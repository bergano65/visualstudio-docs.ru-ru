---
title: "Изолированные параметров точки входа оболочки (C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 13f05a147f0d9ab36d49b93cc91bcbaa7b002c70
ms.lasthandoff: 02/22/2017

---
# <a name="isolated-shell-entry-point-parameters-c"></a>Параметры точки входа изолированной оболочки (C++)
При запуске приложения на основе оболочки Visual Studio, он вызывает начальную точку входа оболочки Visual Studio. Следующие параметры можно переопределить в вызове начальную точку входа оболочки. Описание каждого параметра см. в разделе [. Файлы pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   Имя приложения  
  
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
  
 Шаблон изолированной оболочки Visual Studio создает файл исходного *имя_решения*.cpp, где *имя_решения* имя решения для приложения. Этот файл определяет главную точку входа для приложения, функции _tWinMain. Эта функция вызывает начальную точку входа оболочки.  
  
 Можно изменить поведение приложения, изменив эти параметры при запуске приложения.  
  
## <a name="parameters"></a>Параметры  
 Начальную точку входа оболочки Visual Studio определяет пять параметров. Не изменяйте первые четыре параметра. Пятый параметр принимает список переопределение параметров. Начальную точку входа оболочки вызывается из главной точкой входа приложения.  
  
 Начальную точку входа оболочки имеет следующую сигнатуру.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Если вы не хотите переопределить параметры приложений, оставьте значения параметров переопределяет параметр как указатель null.  
  
 Чтобы переопределить один или несколько параметров, передайте строку Юникода, содержащий параметры для переопределения. Строка является разделенный точками с запятыми список пар "имя значение". Каждая пара содержит имя параметра, чтобы переопределить, следуют знак равенства (=), а затем значение, которое применяется к параметру.  
  
> [!NOTE]
>  Не включайте пробел в строки Юникода.  
  
 Для параметров типа boolean следующие строки представляют значение true; все остальные строки представляют значение false. Эти строки не учитывается.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   вкл.  
  
-   true  
  
-   да  
  
## <a name="example"></a>Пример  
 Чтобы отключить надстройки и изменение расположения проектов по умолчанию для вашего приложения, можно задать последний параметр «AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp».  
  
## <a name="see-also"></a>См. также  
 [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md)   
 [. Файлы pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
