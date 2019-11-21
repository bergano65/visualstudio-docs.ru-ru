---
title: 16bpp Render Target Format Variant | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188592"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp Render Target Format Variant
Для всех целевых объектов отрисовки и буферов фона задается формат пикселей DXGI_FORMAT_B5G6R5_UNORM.

## <a name="interpretation"></a>Интерпретация
 A render target or back buffer typically uses a 32 bpp (32 bits per pixel) format such as B8G8R8A8_UNORM. 32-bpp formats can consume a large amount of memory bandwidth. Because the B5G6R5_UNORM format is a 16-bpp format that's half the size of 32-bpp formats, using it can relieve pressure on memory bandwidth, but at the cost of reduced color fidelity.

 Если этот вариант дает значительный прирост производительности, это с большой вероятностью указывает на то, что приложение потребляет слишком много пропускной способности памяти. You can gain significant performance improvement, especially when the profiled frame had a significant amount of overdraw or alpha-blending.

A 16-bpp render target format can reduce memory band with usage when your application has the following conditions:
- Doesn't require high-fidelity color reproduction.
- Doesn't require an alpha channel.
- Doesn't often have smooth gradients (which are susceptible to banding artifacts under reduced color fidelity).

Other strategies to reduce memory bandwidth include:
- Reduce the amount of overdraw or alpha-blending.
- Reduce the dimensions of the frame buffer.
- Reduce dimensions of texture resources.
- Reduce compressions of texture resources.

Как обычно, необходимо учитывать потери в плане качества изображения, связанные с этими оптимизациями.

Applications that are a part of a swap chain have a back buffer format (DXGI_FORMAT_B5G6R5_UNORM) that doesn't support 16 bpp. These swap chains are created by using `D3D11CreateDeviceAndSwapChain` or `IDXGIFactory::CreateSwapChain`. To work around this limitation, do the following steps:
1. Create a B5G6R5_UNORM format render target by using `CreateTexture2D` and render to that target.
2. Copy the render target onto the swap-chain backbuffer by drawing a full-screen quad with the render target as your source texture.
3. Call Present on your swap chain.

   If this strategy saves more bandwidth than is consumed by copying the render target to the swap-chain backbuffer, then rendering performance is improved.

   GPU architectures that use tiled rendering techniques can see significant performance benefits by using a 16 bpp frame buffer format. This improvement is because a larger portion of the frame buffer can fit in each tile's local frame buffer cache. Архитектуры с плиточной отрисовкой иногда встречаются в GPU для мобильных телефонов и планшетов. За пределами этого сегмента они практически не применяются.

## <a name="remarks"></a>Заметки
 Формат целевого объекта отрисовки DXGI_FORMAT_B5G6R5_UNORM устанавливается при каждом вызове метода `ID3D11Device::CreateTexture2D`, который создает целевой объект отрисовки. В частности, формат переопределяется, когда объект D3D11_TEXTURE2D_DESC, передаваемый в параметре pDesc, описывает целевой объект отрисовки, то есть:

- Для члена BindFlags установлен флаг D3D11_BIND_REDNER_TARGET.

- Для члена BindFlags снят флаг D3D11_BIND_DEPTH_STENCIL.

- Для члена Usage установлен флаг D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Ограничения
 Так как формат B5G6R5 не имеет альфа-канала, альфа-содержимое не сохраняется при использовании этого варианта. Если приложение требует наличия альфа-канала в целевом объекте отрисовки, можно переключиться на формат B5G6R5.

## <a name="example"></a>Пример
 The **16 bpp Render Target Format** variant can be reproduced for render targets created by using `CreateTexture2D` by using code like this:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
