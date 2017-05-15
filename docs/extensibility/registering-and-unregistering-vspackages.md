---
title: "Регистрация и Отмена регистрации VSPackages | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 35
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 73039d6e9bf0db6b3deee00745e21660173f21c0
ms.contentlocale: ru-ru
ms.lasthandoff: 02/22/2017

---
# <a name="registering-and-unregistering-vspackages"></a>Регистрация и Отмена регистрации VSPackages.
Используйте атрибуты для регистрации VSPackage, но  
  
## <a name="registering-a-vspackage"></a>Регистрация VSPackage  
 Атрибуты можно использовать для управления регистрацией из управляемых пакетов VSPackages. Все регистрационные данные содержатся в pkgdef-файл. Дополнительные сведения о регистрации на основе файлов см. в разделе [CreatePkgDef программы](../extensibility/internals/createpkgdef-utility.md).  
  
 Следующий код показано, как использовать атрибуты Стандартная регистрации для регистрации VSPackage.  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Отмена регистрации расширения  
 Если экспериментировали с большим количеством разных VSPackages и удалить их из экспериментального экземпляра, можно просто запустить **Сброс** команды. Найдите **Сброс экспериментального экземпляра Visual Studio** на начальной странице вашего компьютера, или выполните следующую команду из командной строки:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Если вы хотите удалить расширение, которое устанавливается на экземпляр разработки Visual Studio, перейдите к **средства-расширения и обновления**, найдите нужное расширение и нажмите кнопку **удаления**.  
  
 Если для какой-либо причине ни один из этих методов выполняется успешно при удалении расширения, VSPackage сборки из командной строки можно отменить регистрацию следующим образом:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
