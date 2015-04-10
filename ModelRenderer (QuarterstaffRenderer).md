# 3DModelErrors

package com.petealot.tinkersweaponry;

import org.lwjgl.opengl.GL11;

import assets.tw.textures.models.Quarterstaff;
import net.minecraft.client.Minecraft;
import net.minecraft.entity.Entity;
import net.minecraft.item.ItemStack;
import net.minecraft.util.ResourceLocation;
import net.minecraftforge.client.IItemRenderer;

public class QuarterstaffRenderer implements IItemRenderer{
	
	protected Quarterstaff model;
	
	public QuarterstaffRenderer(){
		model = new Quarterstaff();
	}

	@Override
	public boolean handleRenderType(ItemStack item, ItemRenderType type) {
		switch(type){
		case EQUIPPED:
		case EQUIPPED_FIRST_PERSON:
			return true;
		default: return false;
		}
	}

	@Override
	public boolean shouldUseRenderHelper(ItemRenderType type, ItemStack item,
			ItemRendererHelper helper) {
		return false;
	}

	@Override
	public void renderItem(ItemRenderType type, ItemStack item, Object... data) {
		
		switch(type){
			case EQUIPPED:
			case EQUIPPED_FIRST_PERSON:{
			GL11.glPushMatrix();
			
			Minecraft.getMinecraft().renderEngine.bindTexture(new ResourceLocation("tm:itemQuarterstaffModel.png"));
			
			
			
			model.render((Entity)data[1], 0.0F, 0.0F, 0.0F, 0.0F, 0.0F, 0.0625F);			
			GL11.glPopMatrix();
			}
		default:
			break;
		
		}
		
	}

}

