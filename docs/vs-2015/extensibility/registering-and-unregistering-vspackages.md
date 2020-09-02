---
title: Регистрация и Отмена регистрации пакетов VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193820"
---
# <a name="registering-and-unregistering-vspackages"></a>Регистрация и отмена регистрации пакетов VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для регистрации VSPackage используются атрибуты, но  
  
## <a name="registering-a-vspackage"></a>Регистрация пакета VSPackage  
 Для управления регистрацией управляемых пакетов VSPackage можно использовать атрибуты. Все сведения о регистрации содержатся в файле pkgdef. Дополнительные сведения о регистрации на основе файлов см. в разделе [служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 В следующем коде показано, как использовать стандартные атрибуты регистрации для регистрации пакета VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Отмена регистрации расширения  
 Если вы выполнили эксперимент с множеством различных пакетов VSPackage и хотите удалить их из экспериментального экземпляра, можно просто выполнить команду **Reset** . Найдите **Сброс экспериментального экземпляра Visual Studio** на начальной странице компьютера или выполните следующую команду в командной строке:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Если вы хотите удалить расширение, установленное на экземпляре Visual Studio Development, перейдите в **меню Сервис/расширения и обновления**, найдите расширение и нажмите кнопку **Удалить**.  
  
 Если по какой бы то ни было из этих методов не удается удалить расширение, можно отменить регистрацию сборки VSPackage в командной строке следующим образом:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>См. также:  
 [VSPackages](../extensibility/internals/vspackages.md)
