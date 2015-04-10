# 3DModelErrors
package com.petealot.tinkersweaponry;

import net.minecraft.creativetab.CreativeTabs;
import net.minecraft.item.Item;
import net.minecraft.item.ItemStack;
import net.minecraftforge.common.util.EnumHelper;
import cpw.mods.fml.common.Mod;
import cpw.mods.fml.common.Mod.EventHandler;
import cpw.mods.fml.common.SidedProxy;
import cpw.mods.fml.common.event.FMLInitializationEvent;
import cpw.mods.fml.common.event.FMLPostInitializationEvent;
import cpw.mods.fml.common.event.FMLPreInitializationEvent;
import cpw.mods.fml.common.registry.GameRegistry;

@Mod(modid = "tw", name = "Tinkers' Weaponry", version = "1.0")

public class TinkersWeaponry {
	
	public static Item itemPaddedHandle;
	public static Item Quarterstaff;
	
	public static Item.ToolMaterial quarterStaffMaterial = EnumHelper.addToolMaterial("quarterStaffMaterial", 0, 500, 1, 0, 5);
	
	@EventHandler
	public void preInit(FMLPreInitializationEvent event){
		//Item & Block initialisation and registering
		//Config Handling
		itemPaddedHandle = new ItemPaddedHandle().setUnlocalizedName("ItemPaddedHandle").setCreativeTab(tabTinkersWeaponry).setTextureName("tw:itemPaddedHandle");
		Quarterstaff = new ItemQuarterStaff(quarterStaffMaterial).setUnlocalizedName("ItemQuarterStaff").setCreativeTab(tabTinkersWeaponry).setTextureName("tw:itemQuarterStaff").setFull3D();
		
		GameRegistry.registerItem(itemPaddedHandle, itemPaddedHandle.getUnlocalizedName().substring(5));
		GameRegistry.registerItem(Quarterstaff, Quarterstaff.getUnlocalizedName().substring(5));
	
	}
	
	@SidedProxy(clientSide="com.petealot.tinkersweaponry.ClientProxy", serverSide="com.petealot.tinkersweaponry.CommonProxy")
	public static CommonProxy proxy;
	
	@EventHandler
	public void init(FMLInitializationEvent event){
		//Proxy, TileEntity, entity, GUI and Packet Registering
	}
	
	@EventHandler
	public void postInit(FMLPostInitializationEvent event){
		
	}
	
	public static CreativeTabs tabTinkersWeaponry = new CreativeTabs("Tinkers' Weaponry"){
		@Override
		public Item getTabIconItem(){
			return new ItemStack(itemPaddedHandle).getItem();
		}
	};
}

