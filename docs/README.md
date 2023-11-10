# imgui-drawlist (1.89.5)
ImGui, but only DrawList

INIT:
 
    ImGui::CreateContext();
    ImGui_ImplDX11_Init(device, context);

    auto &io = ImGui::GetIO();

    // always init font, because default font deleted.
    tahoma12 = io.Fonts->AddFontFromMemoryCompressedTTF(
      tahoma_regular_compressed_data,
      tahoma_regular_compressed_size, 12.f, nullptr,
      io.Fonts->GetGlyphRangesCyrillic());

PRESENT:

    ImGui_ImplDX11_NewFrame();
    ImGui::NewFrame();

    /* there call functions from draw list */
    draw_list = ImGui::GetBackgroundDrawList();
    draw_list->AddLine(from, to, color);
    /* there call functions from draw list */

    ImGui::Render();
    ImGui_ImplDX11_RenderDrawData(ImGui::GetDrawData());
