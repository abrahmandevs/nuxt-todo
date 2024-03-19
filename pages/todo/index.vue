<template>
  <div>
	<div>
    <div class="m-auto h-full w-full flex items-center justify-center bg-teal-lightest font-sans">
        <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
            <div class="mb-4 space-y-3">
                
                    <h1 class="text-grey-darkest">Hello, </h1>
                <h1 class="text-grey-darkest font-bold">Todo App</h1>
                <form class="" wire:submit.keydown.enter="createTodo()">
                    <input name="addTodo"
                        id="addTodo"
                        wire:model='addTodo'
                        
                        class=" outline-none placeholder:text-black placeholder:text-sm shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker" placeholder="What do  you need to do?">

                    
                    
                </form>
            </div>
            {{$test}}
            <div class="divide-y">
                <div>
                    <div wire:key="defaultTab-{{uniqid()}}">
                        
                </div>
                <div wire:key="activeTab-{{uniqid()}}">

                </div>
                <div wire:key="completedTab-{{uniqid()}}">
                    
                </div>
                </div>
                <div class="py-3 flex justify-between items-center gap-x-2">
                    <button wire:click="checkAllTask" class="">Check All</button>
                    <p class=" text-sm"> items remaning</p>
                </div>
                <div class="py-3 flex justify-between items-center gap-x-2 text-sm">
                    <div class="flex items-center gap-x-1">
                        <button wire:click="allTask('defaultTab')" class="{{$commonClass}} {{1 =='defaultTab' ? 'border' :''}}">All</button>
                        <button wire:click="activeTask('activeTab')" class="{{$commonClass}}  {{2 =='activeTab' ? 'border' :''}}">Active</button>
                        <button wire:click="completedTask('completedTab')" class="{{$commonClass}}  {{3 =='completedTab' ? 'border' :''}}">Complete</button>
                    </div>
					<div class="flex items-center justify-between">
        <label class="shrink-0 flex items-center gap-x-2" for="completed" wire:click="completed('{{$task->id}}','{{$currentTab}}')">
            <input type="checkbox"  id="completed" :value="$task->id" {{ $task->status ==1 ? 'checked' : ''}}>
            <p class="w-full">{{$task->name}} {{$task->id}}</p>
        </label>
        <button type="button" wire:click="deleteTodo('{{$task->id}}')" class="flex-no-shrink p-2 ml-2 text-red border-red">X</button>

    </div>s
                    <button wire:click="clearCompletedTask" class="p-1 px-2 border rounded border-gray-400">Clear completed</button>
                </div>
            </div>

        </div>
    </div>
</div>
  </div>
</template>

<script setup>
</script>