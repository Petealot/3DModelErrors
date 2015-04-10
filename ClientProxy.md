# 3DModelErrors

package com.petealot.tinkersweaponry;

import net.minecraftforge.client.IItemRenderer;
import net.minecraftforge.client.MinecraftForgeClient;

import com.petealot.tinkersweaponry.*;

public class ClientProxy extends CommonProxy{

    @Override
	public void reigsterRenders(){
		MinecraftForgeClient.registerItemRenderer(com.petealot.tinkersweaponry.TinkersWeaponry.Quarterstaff, (IItemRenderer)new QuarterstaffRenderer());
	}
}

