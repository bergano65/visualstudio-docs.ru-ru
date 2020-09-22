---
title: Служебная программа RegPkg | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843033"
---
# <a name="regpkg-utility"></a>Служебная программа RegPkg
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Для регистрации пакетов в Visual Studio предпочтительным способом является использование файлов pkgdef. Это позволяет развертывать расширения без доступа к системному реестру, что является требованием для развертывания VSIX. Файлы pkgdef создаются с помощью [служебной программы CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md). Дополнительные сведения о развертывании пакетов Visual Studio см. в разделе [Доставка расширений Visual Studio](../../extensibility/shipping-visual-studio-extensions.md).  
  
 Служебная программа RegPkg.exe регистрирует пакет VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и готовит его к развертыванию. Эта служебная программа используется в фоновом режиме во время разработки VSPackage. Он выполняется как часть процесса сборки, чтобы вы могли создать и запустить VSPackage в экспериментальном Hive.  
  
 RegPkg может создавать сценарии системного реестра в нескольких форматах. Эти скрипты можно включить в проекты развертывания, такие как MSI-проекты или установщик Windows файлы набора инструментов XML.  
  
 RegPkg.exe обычно находится в \<*Visual Studio SDK installation path*>\VisualStudioIntegration\Tools\Bin\RegPkg.exe. RegPkg соответствует этому синтаксису:  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: корневой каталог  
 Выполняет регистрацию в указанном  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] корневой.  
  
 /regfile: имя файла  
 Создает reg-файл, а не обновляет реестр.  Не может использоваться с/вргфиле или/ргсфиле или/виксфиле.  
  
 /ргсфиле: имя файла  
 Создает RGS-файл, а не обновляет реестр.  Не может использоваться с/вргфиле или/regfile или/виксфиле.  
  
 /вргфиле: имя файла  
 Создает ВРГ-файл, а не обновляет реестр.  Нельзя использовать с/regfile или/ргсфиле или/виксфиле.  
  
 /ргм  
 Создает РГМ-файл в дополнение к RGS-файлу.  Необходимо сочетать с/ргсфиле.  
  
 /виксфиле: имя файла  
 Создает файл, совместимый с набором инструментов установщик Windows XML, вместо обновления реестра.  Нельзя использовать с/regfile или/ргсфиле или/вргфиле.  
  
 /codebase  
 Принудительная регистрация с использованием базы кода, а не сборки.  
  
 /Assembly  
 Принудительная регистрация с использованием сборки, а не базы кода.  
  
 /Unregister  
 Отменяет регистрацию этого пакета.  Не может использоваться  
  
 с/regfile или/вргфиле или/ргсфиле или/виксфиле.  
  
## <a name="see-also"></a>См. также:  
 [Освобождение продукта](../../misc/releasing-a-visual-studio-integration-product.md)   
 [Устранение неполадок регистрации пакета RegPkg](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
