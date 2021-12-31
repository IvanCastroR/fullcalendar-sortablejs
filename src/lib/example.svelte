<script lang="ts">
    import Sortable from 'sortablejs';
	import { onMount } from 'svelte';
   

    let calendarEl;
	let calendar;
    let tasks;

	onMount(async function () {

		calendar = new FullCalendar.Calendar(calendarEl, {
		    initialView: 'dayGridMonth',
            editable: true,
            droppable: true,
            dropAccept: '.list-group-item',
            headerToolbar: {
                left: 'prev,next today',
                center: 'title',
                right: 'dayGridMonth,timeGridWeek,timeGridDay'
            },
		});
		calendar.render();

        createSortable();

	});

    const createSortable = () => {

        new FullCalendar.Draggable(tasks, {
            itemSelector: '.list-group-item',
            eventData: function(eventEl) {
                return {
                    title: eventEl.innerText
                };
            }
        });
        Sortable.create(tasks, {
            group: {
                name: ".list-group-item",
                pull: true,
                put: true
            },
            animation: 150,
            easing: "cubic-bezier(0.895, 0.03, 0.685, 0.22)",
            handle: ".fas",
            chosenClass: "active",
            store: {
               
            },
    
        });
    }


</script>


<div>
    <div class="mx-6">
        <div class="row mt-5">
            <div class="col-3 my-2">
                <h4 class="mb-3">Tasks</h4>

                <div class="list-group"  bind:this={tasks}>

                    <div class="titulo list-group-item list-group-item-success" >
                        <h5 class="mb-0">Tasks low</h5>
                    </div>

                    <div class="list-group-item" >
                        <p><i class="fas fa-grip-lines mr-2"></i>MailGun</p>
                    </div>


                    <div class="list-group-item" >
                        <p class="mb-0"><i class="fas fa-grip-lines mr-2"></i>FullCallendar</p>
                    </div>

                    <div class="titulo list-group-item list-group-item-warning" data-identificador="4">
                        <h5 class="mb-0">Tasks Medium</h5>
                    </div>

                    <div class="list-group-item" >
                        <p><i class="fas fa-grip-lines mr-2"></i> Deploy </p>
                    </div>

                </div>
            </div>

            <div class="col-9">
                <div bind:this={calendarEl} class="calendar-items"/>
            </div>
        </div>
    </div>
</div>

