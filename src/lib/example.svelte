<script lang="ts">
    import Sortable from 'sortablejs';
	import { onMount } from 'svelte';
   

    let calendarEl;
	let calendar;
    let containerEl;

    console.log("INICIANDO")

    // var Calendar = new FullCalendar.Calendar();
    // var Draggable = new FullCalendar.Draggable;

    let tareas;
    console.log("FULLCALENDAR VARIABLES")
    // console.log(Calendar)
    // console.log(Draggable)
	onMount(async function () {

		// calendarEl = document.getElementById('calendar');
        // createSortable();
        
		calendar = new FullCalendar.Calendar(calendarEl, {
		    initialView: 'dayGridMonth',
            editable: true,
            droppable: true,
            // dropAccept: '#external-events div.external-event',
            headerToolbar: {
                left: 'prev,next today',
                center: 'title',
                right: 'dayGridMonth,timeGridWeek,timeGridDay'
            },
            events: [
                // some original fullCalendar examples
                {
                    title: 'All Day Event',
                    start: new Date("2021-12-17")
                },
                {
                    title: 'Long Event',
                    start: new Date("2021-12-20"),
                    end: new Date("2021-12-20")
                },
                {
                    id: 999,
                    title: 'Repeating Event',
                    start: new Date("2021-12-17"),
                    allDay: false
                }
            ],
		});
		calendar.render();

        createSortable();

	});

    const createSortable = () => {
        console.log("crerando sortable")
        new FullCalendar.Draggable(tareas, {
            itemSelector: '.list-group-item',
            eventData: function(eventEl) {
                console.log("eventEl")
                console.log(eventEl)
                return {
                    title: eventEl.innerText
                };
            }
        });
        // Sortable.create(tareas, {
        //     group: {
        //         name: "lista-tareas",
        //         pull: true,
        //         put: true
        //     },
        //     animation: 150,
        //     easing: "cubic-bezier(0.895, 0.03, 0.685, 0.22)",
        //     handle: ".fas",
        //     filter: ".titulo",
        //     // ghostClass: "active",
        //     chosenClass: "active",
        //     //dragClass: "invisible"
        //     dataIdAttr: "data-identificador",
        //     store: {
        //         set: function(sortable){
        //             const orden = sortable.toArray();
        //             localStorage.setItem('lista-tareas', orden.join('|'));
        //         },
    
        //         get: function(){
        //             const orden = localStorage.getItem('lista-tareas');
        //             return orden ? orden.split('|') : [];
        //         }
        //     },
    
        // });
    }


</script>


<div>
    <div class="mx-6">
        <div class="row mt-5">
            <div class="col-3 my-2">
                <h4 class="mb-3">Tasks</h4>

                <div class="list-group" id="tareas" bind:this={tareas}>

                    <div class="titulo list-group-item list-group-item-success" data-identificador="1">
                        <h5 class="mb-0">Tasks low</h5>
                    </div>

                    <div class="list-group-item" >
                        <p><i class="fas fa-grip-lines mr-2"></i>MailGun</p>
                    </div>


                    <div class="list-group-item" data-identificador="3">
                        <p class="mb-0"><i class="fas fa-grip-lines mr-2"></i>FullCallendar</p>
                    </div>

                    <div class="titulo list-group-item list-group-item-warning" data-identificador="4">
                        <h5 class="mb-0">Tasks Medium</h5>
                    </div>

                    <div class="list-group-item" data-identificador="5">
                        <p><i class="fas fa-grip-lines mr-2"></i> Deploy </p>
                    </div>

                </div>
                <!-- <button class="btn btn-sm btn-primary mt-3" id="toggle">Bloquear</button> -->
            </div>

            <div class="col-9">
                <div bind:this={calendarEl} />
            </div>
        </div>
    </div>
</div>

